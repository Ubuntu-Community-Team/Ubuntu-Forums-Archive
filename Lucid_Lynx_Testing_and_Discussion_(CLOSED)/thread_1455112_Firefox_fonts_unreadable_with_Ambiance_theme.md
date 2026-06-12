---
title: "Firefox fonts unreadable with Ambiance theme"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ancanus on 2010-04-15
My major concern is how unreadable firefox is. All the fonts are displayed in a reddish orange over gray background. I've switched to radiance, for now.
Does anyone using Ambiance like the new adjustments?

---

### Post by glasen on 2010-04-15
You can modify the colours by installing a customized "user-chrome.css"-file. This was always necessary when anyone has used one of the Shiki-Colors-themes.

```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

/* Awesomebar improvements */

#urlbar {
    -moz-appearance: textfield !important;
}

#urlbar .autocomplete-textbox-container {
    background-color: -moz-Field !important;
    -moz-appearance: none !important;
}

#urlbar > .autocomplete-history-dropmarker {
    -moz-appearance: toolbarbutton-dropdown !important;
    margin: 0px 3px 0px 5px !important;
}

#PopupAutoCompleteRichResult .autocomplete-richlistitem
{
    background: -moz-Field !important;
}

#PopupAutoCompleteRichResult .autocomplete-richlistitem[selected="true"]
{
    background: Highlight !important;
}

#PopupAutoCompleteRichResult .autocomplete-richlistitem[selected="true"],
#PopupAutoCompleteRichResult .autocomplete-richlistitem[selected="true"] *
{
    color: HighlightText !important;
}

.ac-title
{
    color: -moz-Fieldtext !important;
}

#PopupAutoComplete .autocomplete-treebody {
    background-color: -moz-Field !important;
    color: -moz-Fieldtext !important;
}
```

Just save the above code in the file "~/.mozilla//firefox/????????.default/chrome/userChrome.css" and restart Firefox.

After this modification the background of the awesome-bar is white again.

---

### Post by Atermoon on 2010-04-15
No such thing here :confused:

---

### Post by tjeremiah on 2010-04-15
I actually like the orange font.

---

### Post by coffeecat on 2010-04-15
> **Ancanus said:**
> All the fonts are displayed in a reddish orange over gray background. 

I've just upgraded - just this minute - and I'm not getting this. A pity. I was hoping to see reddish fonts against a grey background.

Could this be a video driver issue? What are you using? Nvidia with proprietary driver here.

---

### Post by Starks on 2010-04-15
Orange text against a grey background on my end.

---

### Post by Atermoon on 2010-04-15
Can you post a screenshot please? I still can't figure out what you're talking about exactly.

---

### Post by Starks on 2010-04-15
Firefox addressbar drop-down.

---

### Post by coffeecat on 2010-04-15
> **Starks said:**
> Firefox addressbar drop-down.

Good grief, is that all? :) I thought from the OP's description...

> **Ancanus said:**
> My major concern is how unreadable firefox is. All the fonts are displayed in a reddish orange over gray background. I've switched to radiance, for now.
Does anyone using Ambiance like the new adjustments?

... that this affected Firefox's menu bar, toolbar and main window.

I like it. It's not at all unreadable on my monitor.

---

### Post by jaco223 on 2010-04-15
I just updated about 30 minutes ago, I haven't noticed this, But I haven't updated
Firefox in a few days because of a sound issue that arose in Firefox several days back.

Jaco

---

### Post by tjeremiah on 2010-04-15
screenshot below

---

### Post by Starks on 2010-04-15
Bug: [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/564303](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/564303)

---

### Post by Ancanus on 2010-04-16
> **coffeecat said:**
> Good grief, is that all? :) I thought from the OP's description...
... that this affected Firefox's menu bar, toolbar and main window.

I like it. It's not at all unreadable on my monitor.

Well, my post was indeed exaggerated!

By 'all fonts' I meant the font used in the area most commonly read of Firefox (excepting the web content.) And by 'unreadable' I meant a serious strain on the eyes.

I guess lowering the brightness to make Ambiance a 'darker' theme makes it even worse.



@Glasen; Starks: Thanks for the workaround and the bug report!

---

