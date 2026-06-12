---
title: "Help synaptic &amp; ubuntu software centre don't work"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by aydee on 2010-03-11
Ubuntu software centre can't find anything to download and when I Atempt to open Synaptic I get This Error:
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


PLEASE HELP!!!!

---

### Post by florus on 2010-03-11
If you go System > Administration > Software Sources
are the various options ticked?

---

### Post by rogue_0111 on 2010-03-11
Try this thread:

[http://ubuntuforums.org/showthread.php?t=855267](http://ubuntuforums.org/showthread.php?t=855267)

---

### Post by coffeecat on 2010-03-11
You have a bad source file with a syntax error:

> **aydee said:**
> E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list

This is probably what is causing both Synaptic and Software Centre to fail.

Go to Places > Computer and double-click on the "File System" icon. Now navigate to /etc/apt/sources.list.d/ and double-click on the playonlinux.list file. This will open read-only in gedit from where you can copy and paste it into your post. Post it so that we can have a look at it, and we can take it from there.

**Edit:** where did you get the instructions for adding the playonlinux repository? Please post a link so that we can see what should have gone in there - or whether there is an error in the instructions.

---

### Post by aydee on 2010-03-12
coffeecat the file says:
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<!-- turing_cluster_prod -->
<html>
<head> <title>  mulx.net  </title>
<meta http-equiv="Keywords" content="">
<meta http-equiv="Description" content="">
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
<link rel="shortcut icon" href="http://spi.domainsponsor.com/favicon/mi_favicon.ico" type="image/x-icon"> 
  <script type="text/javascript">
    
      // **********************************************************************
// AFD
// ********************************************************************** 

    function setupAFDSearchRequest () {
        google_afd_request = {
            channel:     '007341',
            client:      'ca-dp-oversee25_3ph_xml',
            domain_name: 'mulx.net',
            ref:         '',
            hl:          'en',
            q:           '',
            afdt:        afdt,
            token:       afdt
        };
    }

    var totalAds = 0;
    var totalNeededAds = 1;
    var totalWantedAds = 3;
    var ads = '';
    var popularCategories = '';
    var relatedSearches = '';
    var calledAFD = false;
    

    var t_count = 0;  var goo_t_id = '';  var goo_time = 1.5;  var icon_loading = false;
    var goo_ready = false;  var dom_ready = false;  var content_opened = false;  var goo_out = false;  var content_elm = 'ads';   var google_afd_request = {   num_ads: 0,  channel:     '007341',
        client:      'ca-dp-oversee25_3ph_xml', 
        domain_name: 'mulx.net',
        ref:         '',
        hl:          'en',
        kw:          escape(""),
        kw_type:     'broad',
        s:           'mulx.net'
    };   function callAFD () {
        setupAFDSearchRequest();
        callJS();
        calledAFD = true;
    }

    function callJS ( type ) {
        document.write('<script type="text/javascript" language="JavaScript" src="http://pagead2.googlesyndication.com/apps/domainpark/show_afd_ads.js">');
        document.write('<\/script>');

        return true;
    }  function renderAds( source, 
            target, 
            redirectUrl, 
            numberWrittenBefore,
            numberReturned) {

    var numberWritten = 0;

    if ( target == null ) 
    return numberWritten;

    var targetDiv = target;

    if ( source != undefined && source != null ) {
    var currentIndex = 
        numberWritten + numberWrittenBefore;
    
    targetDiv.appendChild ( 
        createGoogleAdElement ( 
            buildAdRedirectUrl ( 
                redirectUrl,
                currentIndex,
                source
            ),
            source,
            source.type
        )
    );
    
    numberWritten++;
    }
    
    return numberWritten;
}

function buildAdRedirectUrl( redirectUrl, currentIndex, currentGoogleAd ) {
    return redirectUrl + 
        '&rank=' + currentGoogleAd.n +
        '&click_display_url=' + escape( currentGoogleAd.visible_url ) +
        '&go_url=' + encodeURIComponent( currentGoogleAd.url );
}   function createGoogleAdElement(url, googleAd, adFormat) {
    var p_wrap = document.createElement( 'p' );  p_wrap.appendChild( createGoogleAdLink( 'span', 'adtitle', googleAd.line1, url, 'nofollow', '_blank', 'doPop=0', googleAd.url ) );   if ( googleAd.line2 ) {
        p_wrap.appendChild(createGoogleAdLine( 'span', 'addesc', googleAd.line2 ));
    }
    if ( googleAd.line3 ) {
        p_wrap.appendChild(createGoogleAdLine( 'span', 'addesc', googleAd.line3));
    }   p_wrap.appendChild( createGoogleAdLink( 'span', 'adurl', googleAd.visible_url, url, 'nofollow', '_blank', 'doPop=0', googleAd.url ) );

    return p_wrap;
}   function createGoogleAdLink( tagName, className, text, url, rel, target, onclick, name, styling ) {
    var link_wrap         = document.createElement( tagName );  
    var link             = document.createElement( 'a' ); 
    link_wrap.className    = className;  
    link.href             = url;
    link.rel             = rel ? rel : '';
       link.target         = target ? target : '';
       link.onclick         = onclick ? onclick : '';
    link.className         = className + "_link";
    link.name            = name ? name : '';
    link.innerHTML         = text;
    link.title            = text;
    link.style.cssText    = styling ? styling : '';
    link_wrap.appendChild( link );
    return link_wrap;
}

function createGoogleAdLine( tagName, className, innerHTML ) {
    var line = document.createElement( tagName );  
    line.className = className;
    line.innerHTML = innerHTML;
    return line;
}

function getParam( name ) {
    var match = new RegExp(name + "=([^&]+)","i").exec( location.search );
    if ( match==null )
        match = new RegExp(name + "=(.+)","i").exec( location.search );
    if ( match==null )
        return null;
    match = match + "";
    result = match.split(",");
    return result[1];
}

/*
 *
 * ContentLoaded.js
 *
 * Author: Diego Perini (diego.perini at gmail.com)
 * Summary: Cross-browser wrapper for DOMContentLoaded
 * Updated: 17/05/2008
 * License: MIT
 * Version: 1.1
 *
 * URL:
 * [http://javascript.nwbox.com/ContentLoaded/](http://javascript.nwbox.com/ContentLoaded/)
 * [http://javascript.nwbox.com/ContentLoaded/MIT-LICENSE](http://javascript.nwbox.com/ContentLoaded/MIT-LICENSE)
 *
 * Notes:
 * based on code by Dean Edwards and John Resig
 * [http://dean.edwards.name/weblog/2006/06/again/](http://dean.edwards.name/weblog/2006/06/again/)
 *
 */

// @w    window reference
// @f    function reference

function ContentLoaded(w, f) {
    var    d = w.document,
        D = 'DOMContentLoaded',
        // user agent, version
        u = w.navigator.userAgent.toLowerCase(),
        v = parseFloat(u.match(/.+(?:rv|it|ml|ra|ie)[\/: ]([\d.]+)/)[1]);

    function init(e) {
        if (!document.loaded) {
            document.loaded = true;
            dom_ready    = true;
            var secondDom = document.getElementById('secondtier_ads_block') ? document.getElementById('secondtier_ads_block') : 0;    
            if ( secondDom ) secondDom.style.display = 'none';
            // pass a fake event if needed
            f((e.type && e.type == D) ? e : {
                type: D,
                target: d,
                eventPhase: 0,
                currentTarget: d,
                timeStamp: +new Date,
                eventType: e.type || e
            });
        }
    }

    // safari < 525.13
    if (/webkit\//.test(u) && v < 525.13) {

        (function () {
            if (/complete|loaded/.test(d.readyState)) {
                init('khtml-poll');
            } else {
                setTimeout(arguments.callee, 10);
            }
        })();

    // internet explorer all versions
    } else if (/msie/.test(u) && !w.opera) {
        d.attachEvent('onreadystatechange',
            function (e) {
                if (d.readyState == 'complete') {
                    d.detachEvent('on'+e.type, arguments.callee);
                    init(e);
                }
            }
        );
        if (w == top) {
            (function () {
                try {
                    d.documentElement.doScroll('left');
                } catch (e) {
                    setTimeout(arguments.callee, 10);
                    return;
                }
                init('msie-poll');
            })();
        }

    // browsers having native DOMContentLoaded
    } else if (d.addEventListener &&
        (/opera\//.test(u) && v > 9) ||
        (/gecko\//.test(u) && v >= 1.8) ||
        (/khtml\//.test(u) && v >= 4.0) ||
        (/webkit\//.test(u) && v >= 525.13)) {

        d.addEventListener(D,
            function (e) {
                d.removeEventListener(D, arguments.callee, false);
                init(e);
            }, false
        );

    // fallback to last resort for older browsers
    } else {

        // from Simon Willison
        var oldonload = w.onload;
        w.onload = function (e) {
            init(e || w.event);
            if (typeof oldonload == 'function') {
                oldonload(e || w.event);
            }
        };

    }
}

function ticker() {
    t_count = t_count + 1;
    goo_time = (goo_time > 0) ? (goo_time - .01) : 0;
    var contentID = '';

    if ( ! goo_ready ) {
        if ( goo_time > 0 ) {
            contentID = setTimeout( function() { ticker() }, 1 );
            if( !icon_loading && dom_ready ) {
                show_loading();
                icon_loading = true;
            }
        } else {
            if ( !dom_ready ) {
                setTimeout( function() { ticker() }, 1); 
                return;
            }
            hide_loading();
            goo_ready = true;
            goo_out = true;
            if ( !content_opened ) open_second();
            if ( contentID ) clearTimeout ( contentID );
            return;
        }
    } else {
        clearTimeout ( contentID );
        return;
    }
}

function show_loading() {
    var d = document.getElementById( content_elm );
    var l_wrap = document.createElement( "DIV" );
    l_wrap.id = 'status';
    l_wrap.setAttribute("style", "position: relative; display: block; width: 100%; height: 25px; padding: 20px 0; text-align: center; background: #ffffff");
    var l_icon = document.createElement( "IMG" );
    l_icon.setAttribute("src", "http://spi.domainsponsor.com/images/icon_loading.gif");
    l_icon.setAttribute("style", "margin: 0 auto; vertical-align: middle");
    l_wrap.appendChild(l_icon);
    if ( d ) d.insertBefore( l_wrap, d.firstChild);
}
function hide_loading() {
    d = document.getElementById( content_elm );
    var icon = document.getElementById('status');
    if ( icon ) d.removeChild( icon );
    return;
}

function google_afd_ad_request_done( response ) {
    if ( response.error_code && ( response.error_code == 200 ) ) {
        return false;
    }  var click_token = response.token ? response.token : '';
    var search_token = response.search_token ? response.search_token: '';

    if( response.ads ) { 
        var google_ads = response.ads;
    } else {
        var google_ads = response;
    }

    var numberAdsReturned = ( google_ads && google_ads.length ) ? google_ads.length : 0;

      goo_ready = true;
    ContentLoaded(window, function (e) { process_goo( response) } );
}

function process_goo ( response ) {  var click_token = response.token ? response.token : '';
    var search_token = response.search_token ? response.search_token: '';  if( response.ads ) { 
        var google_ads = response.ads;
    } else {
        var google_ads = response;
    }

    var numberAdsReturned = ( google_ads && google_ads.length ) ? google_ads.length : 0;

      if ( numberAdsReturned && click_token && search_token ) {
        addToken( click_token, search_token );
    } else if ( calledAFD && click_token && search_token ) {
        addToken( click_token, search_token );
    }
               
    if ( document.getElementById('searchbox_action') && search_token ) {
        document.getElementById('click_token').value = click_token;
        document.getElementById('search_token').value = search_token;
    }     if ( numberAdsReturned < totalNeededAds ) {
        totalAds = numberAdsReturned;  return;
    }    content_opened = true;
}

 function open_second( numberAdsReturned ) {
    var elm_second_display = false;
    var elm_second = document.getElementById('secondtier_ads_block');
    if ( elm_second ) {
        elm_second.style.display = "none";
      if ( ( numberAdsReturned == 0 ) || goo_out || ! goo_ready ) {
         elm_second.style.display = "";
      }
    }
}

 function open_web( numberAdsReturned ) {
               if ( numberAdsReturned > 0 ) {
        var elm_organic = document.getElementById('organic_ads_block');
        if ( elm_organic ) {
          elm_organic.style.display = "";
        }
      }
}

function addToken( click_token, search_token ) {  var allLinks = document.getElementsByTagName('a');
      for( var j=0; j < allLinks.length; j++ ){
        if ( allLinks.item(j).className.match("kw") ) {
            allLinks.item(j).setAttribute('href', allLinks.item(j).href+"&click_token="+click_token+"&search_token="+search_token);
        }
      }
}
    
    var flagsloaded = false;

  function loadFlags () {
      if ( !flagsloaded ) {
          var listel = document.getElementById( "dropdownflag" );   listel.options[0].style.background =  "url('http://spi.domainsponsor.com/images/en.png') no-repeat right";  listel.options[1].style.background =  "url('http://spi.domainsponsor.com/images/es.png') no-repeat right";  listel.options[2].style.background =  "url('http://spi.domainsponsor.com/images/fr.png') no-repeat right";  listel.options[3].style.background =  "url('http://spi.domainsponsor.com/images/zh.png') no-repeat right";  listel.options[4].style.background =  "url('http://spi.domainsponsor.com/images/de.png') no-repeat right";  listel.options[5].style.background =  "url('http://spi.domainsponsor.com/images/pt.png') no-repeat right";  listel.options[6].style.background =  "url('http://spi.domainsponsor.com/images/ja.png') no-repeat right";  listel.options[7].style.background =  "url('http://spi.domainsponsor.com/images/nl.png') no-repeat right";  listel.options[8].style.background =  "url('http://spi.domainsponsor.com/images/it.png') no-repeat right";  listel.options[9].style.background =  "url('http://spi.domainsponsor.com/images/ko.png') no-repeat right";  flagsloaded = true;
      }
  }  function addEvent(obj, evType, fn) { 
        if (obj.addEventListener){ 
            obj.addEventListener(evType, fn, false); 
            return true; 
        } else if (obj.attachEvent){ 
            var r = obj.attachEvent("on"+evType, fn); 
            return r; 
        } else { 
            return false; 
        } 
    }  function addOToken( elm ) {
  var allLinks = document.getElementsByTagName('a');
    for( var j=0; j < allLinks.length; j++ ){
        if ( allLinks.item(j).className.match("kw") ) {
            allLinks.item(j).setAttribute('href', allLinks.item(j).href+"&ot="+elm);
        }
    }

    if ( document.getElementById( 'searchbox_action' ) ) {
        var ot_elm = document.createElement( 'INPUT' );
        ot_elm.value = elm;
        ot_elm.type= 'hidden';
        ot_elm.name = 'ot';
        ot_elm.id = 'ot';
        document.getElementById('searchbox_action').getElementsByTagName('DIV')[0].appendChild( ot_elm );
    }
}
  </script> <script type="text/javascript">
      
          calledAFD = true;
      
          var calledJS = callJS();
          if( calledJS ) ticker();
      </script> 

    
        <link rel="stylesheet" href="http://spi.domainsponsor.com/css/0/landing/en.css" type="text/css">
        
        
        <link rel="stylesheet" href="http://spi.domainsponsor.com/css/41/landing/en.css" type="text/css">
        
         
</head>

<body onunload="exitPop();" class='generic'>
<div id="container">
    <div class="container_wrap">

<!-- BOF Header -->
    <div id="header">  <div id="header_wrap">
    <div id="header_title">   <h1 id="domainname"> Mulx.net </h1>
        <p id="tagline">  What you need, when you need it  <p>  </div>

    <div id="header_links">  <div class="dropdown"> <form action="/" method="POST" name="lang_selection" id="lang_dropdown">
        <div class="lang_dropdown_wrap">
            <input type="hidden" name="epl" value="03240020VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFUEWgQRFQRGQWdRUAxTBQZESFYWWkAIXwxeSwAHQQJcOVUMTREOEUEIV1YSUBBBWxZdShFsWxFECwxWOg9XXANRAFAEB1dSDRNIV0REC1FREAVWA1USBVURCl8LOVoFCVIGRVZWFQRSWkpBCVYAW1EQUVpDQFgIUwc8UQFbAUdHA1YRVl8_FUxFXQVSXhdYEgNUVQpEawZfDQRUADlZEglX">
            <input type="hidden" name="debug" value="0">
            <select id="dropdownflag" name="dropdown_lang" onchange="this.form.submit()" onclick="loadFlags();">  <option value="en" selected> English </option>  <option value="es" > Español </option>  <option value="fr" > Français </option>  <option value="zh" > &#20013;&#25991; </option>  <option value="de" > Deutsch </option>  <option value="pt" > Português </option>  <option value="ja" > &#26085;&#26412;&#35486; </option>  <option value="nl" > Nederlands </option>  <option value="it" > Italiano </option>  <option value="ko" > &#54620;&#44397;&#50612; </option>  </select>
        </div>
    </form> </div>     <p id="links"> <a href="#" onclick="window.external.AddFavorite('http://www.mulx.net','mulx.net');" class="link_bookmark">Bookmark this page</a> <a href="#" onclick="this.style.behavior='url(#default#homepage)';this.setHomePage('http://www.mulx.net');" class="link_homepage">Make this your homepage</a>       </p>  </div>
    <div class="clear">&nbsp;</div>
</div>

<div class="top_break"></div>     <! -- BOF of poptop -->
  <div id="poptop">
      <div class="poptop_wrap">
    <span class="txt_related"> Related Searches </span>  <table>
      <tr> <td class="kwl_1">                              <a href='/?epl=03990052VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=stock%20photo' onclick='doPop=0;' class='kw '>stock photo</a>   </td>             <td class="kwl_2">                              <a href='/?epl=03990053VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4GR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=business' onclick='doPop=0;' class='kw '>business</a>   </td>             <td class="kwl_3">                              <a href='/?epl=03990054VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4HR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=free%20downloads' onclick='doPop=0;' class='kw '>free downloads</a>   </td>             <td class="kwl_4">                              <a href='/?epl=03990047VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4AR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=download%20free%20software' onclick='doPop=0;' class='kw '>download free software</a>   </td>             <td class="kwl_5">                              <a href='/?epl=03990048VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4BR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=stock%20market%20investing' onclick='doPop=0;' class='kw '>stock market investing</a>   </td>             <td class="kwl_6">                              <a href='/?epl=03990049VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4CR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=car%20insurance' onclick='doPop=0;' class='kw '>car insurance</a>   </td>             <td class="kwl_7">                              <a href='/?epl=03990050VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4DR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=life%20insurance' onclick='doPop=0;' class='kw '>life insurance</a>   </td>             <td class="kwl_8">                              <a href='/?epl=03990059VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4MR0MHAkoGDmwRWxUKE1pHFA1UR2dMW0E6WVUMXFALVBIFVREKXws5WgUJUgZFVlYVBFJaSkEJVgBbURBRWkNYURhHDRFcOhVcFEYFUl5RRA4RQQZnCBJCCVxXB2dQAQ4GR0MHAkoGDmwVTRZSXlleDwoTVFRUW0Y6UlsNX1UAbF4SDVM&amp;query=cheap%20auto%20insurance' onclick='doPop=0;' class='kw '>cheap auto insurance</a>   </td> </tr>
    </table>  <div class="clear">&nbsp;</div>
      </div>
  </div>

<! -- EOF of poptop -->   </div>
<!-- EOF Header -->

<!-- BOF Main -->
    <div id="main">
        <div class="main_wrap">

<!-- BOF Sidebar -->
        <div id="sidebar">
            <div class="sidebar_wrap">   <div class="poplinks">
    <ul class="cat_resources">  <li class='keywords_header'><h3>Related Searches</h3></li>                <li class="kwl_1">                              <a href='/?epl=04020028VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FR0MHAkoGDmwRWxUKE1pHFA1UR2dUXV8ORmsOWVcBWloGFgYGSwwBXT5dAgpXBBECAEFQX1dGSFhSUQxdSwxQEgpVGxRXFwJsElsTRQBQCgUSWkVMC2sBQ0ZYC1tcOlpQXAJEEF0EFFAJaxJOE1AKDQhbXh5ZWF0KQmsFV1YCX1E_WhFeCQ&amp;query=stock%20photo' onclick='doPop=0;' class='kw '>stock photo</a>   </li>             <li class="kwl_2">                              <a href='/?epl=04020029VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4GR0MHAkoGDmwRWxUKE1pHFA1UR2dUXV8ORmsOWVcBWloGFgYGSwwBXT5dAgpXBBECAEFQX1dGSFhSUQxdSwxQEgpVGxRXFwJsElsTRQBQCgUSWkVMC2sBQ0ZYC1tcOlpQXAJEEF0EFFAJaxJOE1AKDQhbXh5ZWF0KQmsFV1YCX1E_WhFeCQ&amp;query=business' onclick='doPop=0;' class='kw '>business</a>   </li>             <li class="kwl_3">                              <a href='/?epl=04020030VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4HR0MHAkoGDmwRWxUKE1pHFA1UR2dUXV8ORmsOWVcBWloGFgYGSwwBXT5dAgpXBBECAEFQX1dGSFhSUQxdSwxQEgpVGxRXFwJsElsTRQBQCgUSWkVMC2sBQ0ZYC1tcOlpQXAJEEF0EFFAJaxJOE1AKDQhbXh5ZWF0KQmsFV1YCX1E_WhFeCQ&amp;query=free%20downloads' onclick='doPop=0;' class='kw '>free downloads</a>   </li>             <li class="kwl_4">                              <a href='/?epl=04020023VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4AR0MHAkoGDmwRWxUKE1pHFA1UR2dUXV8ORmsOWVcBWloGFgYGSwwBXT5dAgpXBBECAEFQX1dGSFhSUQxdSwxQEgpVGxRXFwJsElsTRQBQCgUSWkVMC2sBQ0ZYC1tcOlpQXAJEEF0EFFAJaxJOE1AKDQhbXh5ZWF0KQmsFV1YCX1E_WhFeCQ&amp;query=download%20free%20software' onclick='doPop=0;' class='kw '>download free software</a>   </li>             <li class="kwl_5">                              <a href='/?epl=04020024VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4BR0MHAkoGDmwRWxUKE1pHFA1UR2dUXV8ORmsOWVcBWloGFgYGSwwBXT5dAgpXBBECAEFQX1dGSFhSUQxdSwxQEgpVGxRXFwJsElsTRQBQCgUSWkVMC2sBQ0ZYC1tcOlpQXAJEEF0EFFAJaxJOE1AKDQhbXh5ZWF0KQmsFV1YCX1E_WhFeCQ&amp;query=stock%20market%20investing' onclick='doPop=0;' class='kw '>stock market investing</a>   </li>  </ul>  </div>       </div>
        </div>
<!-- EOF Sidebar -->

<!-- BOF Keywords -->
        <div id="content">
            <div class="content_wrap"> <a class="kw" onclick="doPop=0;" href='/?epl=03180072VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFUEWgQRFQRGQWdRUAxTBQZEV0kRDlsPFgMWTAoSVhJAOVgTQV4OD2pcXAUDBlIGBVIOCl0VRA5AFw1cABQODlIAERBQVhMCXWpIV0cMB1pARFxcFlpTD28LBwVRVxUCVRJSBFpFGFxSUFZdRlgGE0cOUVoAbF0FDVBFSwAHQQJcOUMaRVJcDVxbUx5VXQlaQz1fVgpUWARvCBAFVA&query=botsearch09' style="display: none">stock photo</a>     <!-- BOF popmain -->
    <div class="popmain">   <ul class="cat_popular">   <li class="header">Related Searches</li>   <li> <ul id='popmain_kw_0'>                 <li class="kwl_1">                              <a href='/?epl=04000054VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=stock%20photo' onclick='doPop=0;' class='kw '>stock photo</a>   </li>               <li class="kwl_2">                              <a href='/?epl=04000055VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4GR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=business' onclick='doPop=0;' class='kw '>business</a>   </li>               <li class="kwl_3">                              <a href='/?epl=04000056VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4HR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=free%20downloads' onclick='doPop=0;' class='kw '>free downloads</a>   </li>            <li class='clearRow' style='width:100%'>&nbsp;</li>       <li class="kwl_4">                              <a href='/?epl=04000049VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4AR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=download%20free%20software' onclick='doPop=0;' class='kw '>download free software</a>   </li>               <li class="kwl_5">                              <a href='/?epl=04000050VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4BR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=stock%20market%20investing' onclick='doPop=0;' class='kw '>stock market investing</a>   </li>               <li class="kwl_6">                              <a href='/?epl=04000051VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4CR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=car%20insurance' onclick='doPop=0;' class='kw '>car insurance</a>   </li>            <li class='clearRow' style='width:100%'>&nbsp;</li>       <li class="kwl_7">                              <a href='/?epl=04000052VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4DR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=life%20insurance' onclick='doPop=0;' class='kw '>life insurance</a>   </li>               <li class="kwl_8">                              <a href='/?epl=04000061VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4MR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=cheap%20auto%20insurance' onclick='doPop=0;' class='kw '>cheap auto insurance</a>   </li>               <li class="kwl_9">                              <a href='/?epl=04000062VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4NR0MHAkoGDmwRWxUKE1pHFA1UR2dVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIUxIORUELZwQXFlldAV1mDFcJUxYRBlkXBVs_QB9HBghbCA9eE1lUWF4SalMNV14JVmsLQ19S&amp;query=credit%20card' onclick='doPop=0;' class='kw '>credit card</a>   </li>            <li class='clearRow' style='width:100%'>&nbsp;</li>       <li class="kwl_10">                              <a href='/?epl=04020078VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FURYRBlkXBVs_RAlEXkVYERRZVEpnWVAMW2sOWVcBWloGFgYGSwwBXT5dAgpXBBECAEFQX1dGSFhSUQxdSwxQEgpVGxRXFwJsElsTRQBQCgUSWkVMC2sBQ0ZYC1tcOlpQXAJEEF0EFFAJaxJOE1AKDQhbXh5ZWF0KQmsFV1YCX1E_WhFeCQ&amp;query=call%20center' onclick='doPop=0;' class='kw '>call center</a>   </li>          </ul> <li>
      </ul>  <div class="clear">&nbsp;</div>
    </div>

    <div class="clear">&nbsp;</div>
<!-- EOF popmain -->    <!-- BOF popmain generic -->
    <div class="popmain_generic"> <!-- BOF popgeneric -->  <ul class="cat_favorite">  <li class="header">  Popular Categories  </li>                    <li>    <span class="keyword_header">Travel</span>    <ul class="sub">      <li class="kwl_1">                              <a href='/?epl=03980021VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Airline%20tickets' onclick='doPop=0;' class='kw '>Airline tickets</a>   </li>                        <li class="kwl_2">                              <a href='/?epl=03980022VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4GR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Hotels' onclick='doPop=0;' class='kw '>Hotels</a>   </li>                        <li class="kwl_3">                              <a href='/?epl=03980023VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4HR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Car%20rental' onclick='doPop=0;' class='kw '>Car rental</a>   </li>                        <li class="kwl_4">                              <a href='/?epl=03980016VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4AR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Flights' onclick='doPop=0;' class='kw '>Flights</a>   </li>                        <li class="kwl_5">                              <a href='/?epl=03980017VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4BR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=South%20Beach%20Hotels' onclick='doPop=0;' class='kw '>South Beach Hotels</a>   </li>  </ul>     </li>              <li>    <span class="keyword_header">Finance</span>    <ul class="sub">      <li class="kwl_1">                              <a href='/?epl=03980021VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Free%20credit%20report' onclick='doPop=0;' class='kw '>Free credit report</a>   </li>                        <li class="kwl_2">                              <a href='/?epl=03980022VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4GR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Online%20Payment' onclick='doPop=0;' class='kw '>Online Payment</a>   </li>                        <li class="kwl_3">                              <a href='/?epl=03980023VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4HR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Credit%20Card%20Application' onclick='doPop=0;' class='kw '>Credit Card Application</a>   </li>                        <li class="kwl_4">                              <a href='/?epl=03980016VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4AR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Car%20Insurance' onclick='doPop=0;' class='kw '>Car Insurance</a>   </li>                        <li class="kwl_5">                              <a href='/?epl=03980017VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4BR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Health%20insurance' onclick='doPop=0;' class='kw '>Health insurance</a>   </li>  </ul>     </li>              <li>    <span class="keyword_header">Home</span>    <ul class="sub">      <li class="kwl_1">                              <a href='/?epl=03980021VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4FR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Foreclosures' onclick='doPop=0;' class='kw '>Foreclosures</a>   </li>                        <li class="kwl_2">                              <a href='/?epl=03980022VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4GR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Houses%20For%20Sale' onclick='doPop=0;' class='kw '>Houses For Sale</a>   </li>                        <li class="kwl_3">                              <a href='/?epl=03980023VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4HR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Mortgage' onclick='doPop=0;' class='kw '>Mortgage</a>   </li>                        <li class="kwl_4">                              <a href='/?epl=03980016VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4AR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=People%20Search' onclick='doPop=0;' class='kw '>People Search</a>   </li>                        <li class="kwl_5">                              <a href='/?epl=03980017VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBwJcBBIWXUoRbF0FDVRTCkMJQxUJCVlFVEIVDkFQS0xrXhVBXQ1WZgxXCVYHVVAJVVAAWRIWWBNAWQUERwhXXlIXDkJrEFlXDg4BR0MHAkoGDmwRWxUKBFBZBBNcVmdVVVgLalgDVl0MXVNHVAcQUQIIbAhQWwNSE1QAFVBSV0pNDAJQWgdKUAYVXwRJFQxKATlADkEUVAYIVAAValhNHkddDFZRPVFdWAESElUDEVsNOUcYRAMKD1xZCkdUWVRXQ24CWlsFVFw6WUdcAQ&amp;query=Real%20Estate%20Training' onclick='doPop=0;' class='kw '>Real Estate Training</a>   </li>  </ul>     </li>   </ul>
  <div class="clear">&nbsp;</div>
<!-- EOF popgeneric --> </div>
        <div class="clear">&nbsp;</div>
<!-- EOF popmain generic -->    <div class="search"> <div class="search_box">
  <form id="searchbox_action" action="/" method="POST" onSubmit="doPop = 0;" >
    <div>
    <input type="hidden" name="epl" value="03710085VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFUEWgQRFQRGQWdRUAxTBQZEV0kRDlsPFgMWTAoSVhJAOVgTQV4OD2pcXAUDBlIGBVIOCl0VRA5AFw1cABQODlIAERBQVhMCXWpIV0cMFlBVEFtROlFbGW8OAlYBD10GEgJSEFxQDz5cUQUMBRcGVEAHX1YXSgkGVQwGSgwFFQpRH0AMR1M_ElpASltRDBZQVRBbUQdcTEdDDgpbADlaBQlUERBQVhMCXWpMQURUWFNbEFUfBF9YDkc9BFcKAV8EawxEXgQ">
    <input type="hidden" name="debug" value="0">
    <input type="hidden" name="search_token" id="search_token" value="">
    <input type="hidden" name="click_token" id="click_token" value="">  <input type="text" name="query" class="text" value="">  <div class="submit_wrap">
        <input type="submit" value="Search" class="submit">
        </div>  </div>
  </form>
</div> </div>  </div>
        </div>
<!-- EOF Keywords -->
        <div class="clear">&nbsp;</div>

        </div>
    </div>
<!-- EOF Main -->

<!-- BOF Footer -->  <div id="footer">    <div class="footer_wrap">         </div>   </div>  <!-- EOF Footer -->

    </div>
</div> <div class="sub_wrap" id="placeholder">     <img src="/?epl=03390013VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwJeBFEEAFZQE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFUEWgQRFQRGQWdRUAxTBQZESFYWWkAIXwxeSwAHQQJcOVUMTREOEUEIV1YSUBBBWxZdShFsWxFECwxWOg9XXANRAFAEB1dSDRNIV0REC1FREAVWA1USEVgDEF1YClwAUEBTBkZeBg9qXFwFAABDVlUWXV4KQU1cVwcNXRcPUEdHCl4AUGgIBQgHHktRUBdWXD1MQBVWCQdfEA4eBApfDkM5UAxaUA0Eal9LBQU" height="1" width="1" alt="">   <script type='text/javascript'> 
    dom_ready = true;
    addOToken('1');   </script>     <script type="text/javascript">
//<!--
var doPop = 1;
function exitPop() {
    if (doPop) {  }
}
//-->
</script>  </div> <!-- Design ID 41 -->
<!-- Slice ID 2 -->
<!-- Test ID 602 -->
<!-- page_complete -->
</body>
</html>

---

### Post by aydee on 2010-03-12
Also to coffeecat, I got that error when I started up synaptic and every time. synaptic also won't turns off when I press close on the error box.

---

### Post by aydee on 2010-03-12
[florus]("http://ubuntuforums.org/member.php?u=454057") I coulsdn't find anything even related to "various options", could you explain more. Thank you for the help though, it is appreciated

---

### Post by florus on 2010-03-12
Sorry, I meant that you should get a list of the available repositories under the 'Ubuntu Software' tab: eg Canonical supported Open Source software (main). These are the repositories that both Synaptic and the Ubuntu Software Centre access to download programs. The first four on the list should be ticked i.e. main, universe, restricted and multiverse, although main is the most important.

---

### Post by plucky on 2010-03-12
That is not a sources.list file,it is just a .html file.

From a terminal ```
sudo rm /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
```

To add the playonlinux repository,assuming you are running Karmic,from a terminal ```
sudo wget http://deb.playonlinux.com/playonlinux_karmic.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
```

Copy and paste one line at a time.

You can now install playonlinux.

Good Luck

---

### Post by coffeecat on 2010-03-12
@aydee, I'm not surprised both Synaptic and Software Center choked when presented with that lot! Anyway, plucky has given you the fix.

As a point of information, so long as you are running Karmic, your playonlinux.list file should consist of one line, viz:

```
deb http://deb.playonlinux.com/ karmic main
```

A bit shorter than what you had! :wink:

---

### Post by aydee on 2010-03-14
Ladies and Gentlemen,
I thank you all very much for your help, everything is now working fine!!!!!!!
 
 
Aydee

---

