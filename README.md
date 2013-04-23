Info
===

I got tired of writing out the same code for the "info" sections of every project I made, so I decided to write a little helper "class" that would put the info container and the info button in the DOM for me.

That's all great right there, but wouldn't it be better if it would automatically populate it with text, html, Markdown, or even content from an external README file? Yes, yes it would be. So I did that, too.

And if you don't trust Info to create and style the elements for you, then feel free to just pass in the HTML Elements or their IDs as strings and Info will use what you've already got set up.

I've got some more info below, but jump on over to [http://tbaldw.in/info](http://tbaldw.in/info) if you want to see it in action.

--------

So, it's super easy to set up. Include the `info.js` and `info.css` files. Then just type a little bit of code:

	new Info();

Did you get that? Okay, this only works if you have your info element just the way you want it. It'll need an id of "info" and the rest of your content will need an id of "container". If your situation isn't this easy, not to fear, there are several options you can pass in.

	new Info({
		url: "README.md",
		el: document.getElementById("more"),  // or just pass in the id as a string
		container: "wrapper",
		btn: "open_info_btn",
		keyTrigger: true
	});

This snippet will load asynchronously in Markdown from "README.md". It can tell it's markdown by the "md" extension, so it runs it through a converter, and populates the element passed in as `el`. It assigns a click event handler to the element passed in as `btn` which opens and closes the info section by sliding over the element passed in as `container` - so make sure your `el` element resides outside of your `container` element. When the `keyTrigger` option is set to true, it lets the user open and close the info section with the letter i.

You can also pass in `text` or `html`. If the text you've passed in is Markdown, you should set `isMarkdown` to `true`.

If using Markdown, the Markdown.Converter.js file is required as a dependency: [https://code.google.com/p/pagedown/wiki/PageDown](https://code.google.com/p/pagedown/wiki/PageDown).

Finally, you can add or edit the styles. The `btn` element is assigned a class of "info_btn". The `el` element is assigned a class of "info_container". And the `container` element is assigned a class of "content_wrapper". (What's that? Those are the best names you've ever heard? Why thank you.) When the info section is open a class of "open" is added to the `el` element, and a class of "inactive" is added to the `container` element. So target those to change the styling if you'd like. If you need help, just look at info.css for reference.