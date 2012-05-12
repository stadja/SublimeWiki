Sublime Wiki
------------
A simple way to maintain a personal wiki in Sublime Text 2. 

This extension isn't designed to replace wikipedia, or even go on the web at all. This is a flat-file, no-nesting, no-nonsense system designed purely to give you (well, me) a place to catch fleeting thoughts and turn them into something useful. To keep it as fiddle-proof as possible, the list of features is intentionally kept very small.

In other words, It's job is to let you maintain a *personal* wiki without spending too much time on it. 
Thanks to Andy Hunt for the inspiration. If you haven't yet, I strongly recommend you read [Pragmatic Thinking and Learning](http://www.amazon.com/gp/product/1934356050?ie=UTF8&tag=httpnatedicco-20&linkCode=shr&camp=213733&creative=393185&creativeASIN=1934356050&ref_=sr_1_1&qid=1335329539&sr=8-1) for more excellent tips on how to really use your brain.
##How It Works
1. Create a directory where you want to keep all your files. I recommend setting this up in [DropBox](http://db.tt/WW19iU5) or some similar service so it auto-syncs across your computers.
2. in Sublime Text, Add your new Personal Wiki folder to a project and save that project. There! That doesn't do much, but it does make your sidebar list all your wiki pages for you.
3. Create a file with a name like `MainIndex.wiki` in that directory. The name isn't important, the extension is. Write some stuff in that file, and make sure to put in some `WikiWords`.
4. Any `WikiWords` (i.e. UpperCamelCase) will be converted to internal links.
   * By default, `Ctrl+F11` is the keystroke to folow a wiki link
   * If a file doesn't exist, you'll be given a new buffer with the default text for a new page.
   * if the file does exist it's opened. Yeah.
5. This system is sparse by design. There are only five things that get marked:
   * WikiLinks
   		* These are identified as `markup.underline.internal.link.Wiki`. You may need to add style rules to your favorite theme to have it render.
	* Markdown-style `**bold** __markings__` are used. 
		* Identified as `markup.bold.Wiki`
	* For that matter, Markdown-esque `_italic_ *strings*` are also supported.
		* Identified as `markup.italic.Wiki`
	* "Double Quoted Strings"
		* Identified as `string.quoted.double.Wiki`
	* URL links
		* Identified as `markup.underline.external.link.Wiki`.

##If Things Aren't Getting Highlighted

It's very possible that your favorite theme doesn't define styles for `markup.bold`, `markup.italic`, or even `markup.underline.internal.link` (although most themes catch that one, because it has `link` in it.)
If this is the case you can edit your theme file pretty easily, and I've included a snippet to make it even easier.

All themes are stored as `.tmTheme` files, which are really just `.plist` files that have been renamed, which are really just `.xml` files. 

*ANYWAY*

To add style rules for **bold** and *italic* wiki text to your favorite theme simply follow these steps:

1. Open `favoriteTheme.tmTheme` in Sublime Text 2
2. Do a quick search for `markup.italic` or `markup.bold` and make sure it's not there.
3. Place your cursor between two `<dict>` elements.
4. Type `dict{enter}` and the snippet should pop up.
5. Type "bold" (or italic) into the first completion slot. Watch the fancy joy of snippets that re-use one variable.
	* Note that one place where your bold or italic choice gets used is the `<fontStyle>` element. Make sure you're typing something that actually __is__ a font style here. If you stick with bold or italic you should be fine. 
6. Hit tab to go to the color slot. This is where you decide what color works for you, and it has to be in hex. 
7. Save the file and restart ST2.

Now all your `**bold**` text should be bold and all your `_italic_` text should be slanty. It's just that easy.

##How You Could Help
1. I would like to make the WikiWords linker more robust, and possibly find a way to have it identify any words that are the names of other pages in the directory, so that you could use any word as a keyword, á la [Tomboy](http://projects.gnome.org/tomboy/).
