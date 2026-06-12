---
title: "Thunderbird doesn't open links in browser (or at all)"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mrowth on 2010-04-28
When I click on an http link in Thunderbird, nothing at all happens. There's no error message on the console, there's no new browser starting, and there's no new tab opening with the browser already running. 

I've tried: sudo update-alternatives --config x-www-browser, choosing firefox.

I've tried: adding a new string value to Thunderbird's warranty-voiding config, network.protocol-handler.app.http, setting it to /usr/bin/firefox as recommended in various threads.

But no luck.

There's an entry for https - firefox on the Attachment tab of the preferences, and https links are indeed opening in Firefox. But not http.

I would welcome any help.

KDE 4.4.2 default mail client and browser are Thunderbird 3.0.4 and Firefox 3.6.3 from the repositories.

---

### Post by Curtiss on 2010-04-28
I had the same problem with lucid lynx I remember seeing a thread in this fourm about it but cant remember if there was a fix. But I went back to using Evolution and I like it better any way. Sorry wasnt of much help.

Good luck.

---

### Post by Wobblybob on 2010-04-28
Try this,
Open Thunderbird and from the menu select [Edit], [Preferences] then [Advanced], [General]

Select [Config Editor] and in the [Filter] box type;

network.protocol-handler.app.http

and check for the matching key in the list, if it does not exist [right click] on the[Config Editor] page, select [New], then [String] In the dialogue box called [Enter preference name] type or copy & paste the following;

network.protocol-handler.app.http

In the next dialogue box called [?network.protocol-handler.app.http] type;

/usr/bin/firefox

---

### Post by randomizer101 on 2010-04-28
Isn't it common sense that it would, by default,open the link using the default browser? Or is it logical to force the user to edit the configuration for such an obvious feature? Granted, the only "problem" I had was that it did not know which program to use by default and I had to pick from a list (which only had Firefox in it). It remembered the selection after that. So this must be a bug.

---

### Post by mrowth on 2010-04-28
> **Wobblybob said:**
> Try this,
Open Thunderbird and from the menu select [Edit], [Preferences] then [Advanced], [General]

Select [Config Editor] and in the [Filter] box type;

network.protocol-handler.app.http

and check for the matching key in the list, if it does not exist [right click] on the[Config Editor] page, select [New], then [String] In the dialogue box called [Enter preference name] type or copy & paste the following;

network.protocol-handler.app.http

In the next dialogue box called [?network.protocol-handler.app.http] type;

/usr/bin/firefox
Thanks for the suggestion, but I wrote in my post that I had already tried that. It didn't help.

---

### Post by mrowth on 2010-04-28
> **randomizer101 said:**
> Isn't it common sense that it would, by default,open the link using the default browser? Or is it logical to force the user to edit the configuration for such an obvious feature? Granted, the only "problem" I had was that it did not know which program to use by default and I had to pick from a list (which only had Firefox in it). It remembered the selection after that. So this must be a bug.
I agree. If there were an option for this, it should be set to the default browser*. However, there's no such option at all, so I don't even know where to pick Firefox from a list. Creating the network.protocol-handler.http.app string doesn't help either. And /usr/bin/firefox does exist. I believe if I could add http handling to where https already is ("Attachments" preferences, strangely), this problem might be solved. I'll look into this with a text editor.

(* though different apps often seem to have different ideas as to just what the default browser **is**)

---

### Post by randomizer101 on 2010-04-28
Regarding that list, it just popped up a window with Firefox and a browse button. It's the same thing you get when using a non-standard protocol in Firefox like Steam:// for the first time.

---

### Post by mrowth on 2010-04-28
> **randomizer101 said:**
> Regarding that list, it just popped up a window with Firefox and a browse button. It's the same thing you get when using a non-standard protocol in Firefox like Steam:// for the first time.

Hrmph! Didn't happen for me.

---

