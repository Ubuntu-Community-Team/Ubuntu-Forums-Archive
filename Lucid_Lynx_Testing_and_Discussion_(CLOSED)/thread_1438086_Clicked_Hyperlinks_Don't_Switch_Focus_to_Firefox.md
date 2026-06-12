---
title: "Clicked Hyperlinks Don't Switch Focus to Firefox?"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by linux4me on 2010-03-24
I'm not sure if this is a change in the UI for Lucid, a bug, or a configuration setting somewhere that I have overlooked, but when I click a hyperlink in Evolution or Ctrl+click a hyperlink in Open Office, the links are opened in a new tab in Firefox, but the focus isn't switched to Firefox. I have to manually Alt+Tab to Firefox to see the web page that is opened. 

In Firefox, I have "When I open a link in a new tab, switch to it immediately" selected, and in Preferences -> Preferred Applications I have "Open link with browser default" selected. Is there another setting somewhere that will switch the focus to Firefox when a link is opened that I am missing?

---

### Post by emarkay on 2010-03-24
FWIW, I had this issue in Thunderbird, but it's all OK here in OO.
Confirm your "Preferred Applications" are what you want them to be.

---

### Post by Anduu on 2010-03-25
I have noticed the same thing.If Firefox isn't running it will launch and display the link however if FF is already running it will not switch focus.

---

### Post by linux4me on 2010-03-25
> **emarkay said:**
> FWIW, I had this issue in Thunderbird, but it's all OK here in OO.
Confirm your "Preferred Applications" are what you want them to be.
Yes, Preferred Applications shows Firefox as the browser of choice and defaults to the settings in FF which I mentioned above.

I went ahead and reported it as a [bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/546969/?loggingout=1"), even though I found [this]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/481541"). I guess for some it's the desired behavior.

---

