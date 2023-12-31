# starling-replay-web-page

*This is a proof of concept plugin for WordPress to display embeded WACZ files.*

# shortcodes method
This plugin uses wordpress's [shortcodes](https://www.smashingmagazine.com/2012/05/wordpress-shortcodes-complete-guide/) to [embed a replayweb.page](https://replayweb.page/docs/embedding) component into WordPress.

This plugin will 
- enable `.wacz` and `.warc` file uploads for WordPress
- add ui.js from the CND to show replayweb.page components
- host a `/replay` folder with `sw.js` pointing to the CND and map it correctly
- reference wacz files in `media library` or using an external path.

## Attributes
`remote_url`: Url to WACZ file that was not uploaded through WordPress media library  

`media_id`: WordPress media library's `id` for WACZ file to display. The `id` is assigned by WordPress when media is uploaded. You can get this number by opening the WACZ file in WordPresses `Media Library` then looking at the address bar. You will see the end of the address ass `id=49`. In this example the media_id is `49`.

`height`: Height of element. Default is `400px`  

`width`: Width of element. Default is `100%`  

`url`: Url inside the WACZ file to display. If not set WACZ index will be shown on load  

`embed`: Embed mode to use. See [Embed Modes](https://replayweb.page/docs/embedding#embed-modes)  
 
### Example:

Link to a WACZ file hosted somewhere else and set height to 100%  
`[wacz_url remote_url="http://someurl.com/somefile.wacz" height="100%"]`

Reference a WACZ file uploaded to WordPress and use the `replay-with-info` embed mode  
`[wacz_url media_id="56" embed="replay-with-info"]`


# javascript method

This plugin also exposes the `starling_replaywebpage` function which has the same functionality as the shortcode method. It takes a dict of attributes just like above.

## Example

```
<script>
document.write(starling_replaywebpage ( { media_id:"56", height:"600px" }))
</script>
```

## Using this plugin

Clone the repo, then place all files in folder called `starling-replay-web-page`. Zip the `starling-replay-web-page` folder so the top level of the ZIP only has this folder. Upload to WordPress's plugin section and activate.

When editing a page, add the `Short Code` element at the desired location. Enter the short code as described above.
