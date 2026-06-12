---
title: "Lucid: Firefox 'Send Link..' does not work"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by 4partee on 2010-05-23
This is a fresh install, only hours old, with the majority of those hours trying to figure this out.  

I used synaptic to install thunderbird. I copied .mozilla and .mozilla-thunderbird from my previous 9.04 installation.  

In firefox, when I click on file, send link..., nothing happens.  In 9.04, the Compose window of Thunderbird would open.

There is nothing about this in any /var/log/ file.

How can I get 'Send Link...' to work again?

John

---

### Post by wheezer on 2010-07-29
I have the same problem with new firefox 3.6.8 and thunderbird 3.1. No fixes I have found work. I am still in 9.10.  Did you find any solution?

---

### Post by Sidewinder1 on 2011-02-27
I am necromancing, I know, please forgive if this has been answered elsewhere. I am having the same problem as above; worked fine in Hardy and I've checked every screen in FF preferences, add-ons, etc. Any assistance would be greatly appreciated.

Tia,
Side

---

### Post by Sidewinder1 on 2011-03-06
Shameless bump...
Can't fathom that no one else is experiencing this problem; probably just me and the guys / gals above.
Either that or the solution is so simple that I'm just an idiot; won't be the first time :D.

---

### Post by grizzler on 2011-03-06
You could try this:

Visit Firefox' configuration page about:config and filter on **network.protocol-handler.external.mailto**. This should be **true**.

Then open Firefox' Preferences window on the Application tab and enter **mailto** in the search field. Make sure the action set is to use Thunderbird.

---

### Post by Sidewinder1 on 2011-03-06
Thank you so much for the response grizzler. I followed your instructions the the letter and both settings were already set to the parameters you specified. I have even tried the "Send Link" function with Thunderbird already running, to no avail. It's probably something relatively simple, but it's frustrating nonetheless.
Again, many thanks.

Side

---

### Post by grizzler on 2011-03-06
Right. Another thing to try. Open the Configuration Editor (gconf-editor) and go to desktop/gnome/url-handlers/mailto. The command specified should be **thunderbird %s** and enabled should be set.

---

### Post by Sidewinder1 on 2011-03-06
Thanks again, followed above and it was already set as you specified... Grrrrrr...
Side

---

### Post by grizzler on 2011-03-07
Still one more setting to check, this time in Thunderbird. Open the Preferences window and go to the Advanced tab. Now open the Configuration Editor and filter on **network.protocol-handler.expose.mailto**. This should be **true**.

That's the last one I can think of...

If this doesn't help and you use add-ons, you could try checking if any of them could be the culprit. Switch them all off and see if it still doesn't work. If it does, activate them one by one until things fail again.

---

### Post by Sidewinder1 on 2011-03-10
Grizz, thanx for your time and patience; it is greately appreciated. Alas, no joy. I'm wondering if it's some sort of 'bug' relating to my (and very few others) exact configuration.
I checked "[B]network.protocol-handler.expose.mailto" 
[/B]and it was already configured as 'true', I then checked further, per your instructions.
Since I'm a winbloze hater my system has only what I consider to be the absolutely necessary additions. I have no add-ons, and the only extensions are: adblock-plus, noscript and two other totally unrelated ones. 
At this point, I do believe it's a Firefox and Gnome and Thunderbird issue and since it's affecting so few, in the grand scheme of things, I will not submit as a bug-report. 
I'll just wait patiently and in the mean time, get "reused" to copy / paste.
Again, thank you for all of your time and efforts; you are definitely a credit to all Linux / Ubuntu users! :D

Side

---

### Post by grizzler on 2011-03-12
> **Sidewinder1 said:**
> Grizz, thanx for your time and patience; it is greately appreciated. Alas, no joy. I'm wondering if it's some sort of 'bug' relating to my (and very few others) exact configuration.
Probably. I can't think of anything else it could be.

Just out of curiosity, does clicking a link in Thunderbird itself work? I.e. if you have a message in one of Thunderbird's windows that contains an e-mail link (e.g. [email]address@domain.tld[/email]), does clicking that make Thunderbird open a window to compose a new message?

---

### Post by Sidewinder1 on 2011-04-09
Grizz, I haven't ever seen a *@*.tld in any email sent to me. If it helps "mailto" opens the T-bird compose page just as http/https... opens a new tab in Firefox.
I'm still wrestling with the "Send Link" in FF, not functioning; I am a tenacious ba$trd but if I am not successful within the next couple of weeks, I'll submit it to Launchpad; I've never done that before so if someone knows the exact procedure for that it would also be helpful.
Guess that actually says something about Ubuntu and FOSS; for me, everything has worked almost perfectly since 2007!
Thanks to all!!!

Side

---

### Post by Sidewinder1 on 2011-04-10
I FOUND THE SOLUTION! At least in my case. After all of the hours of trial and error, including reconfiguring about:config the answer was unbelievably simple.

Apparently, upon upgrade from Hardy to Lucid, via update mgr. (I know, I know, now many of you will chastise me for not doing a clean install to Lucid) some of the environmental variables were changed. See post #4

One of the first places I looked was System-->Preferences-->Preferred Applications, under Mail Reader: Thunderbird, command: _*with environment variables*_, was already listed so I looked elsewhere.......

The solution, finally, was to click on that drop-down box, click on Thunderbird (it then rewrote different environmental variables!!) and close. Voila! Now send link opens the T-bird compose/write page.

4partee, I hope that this works for you; if so, please mark the thread as "Solved" as I cannot, since I didn't start the thread.


Side

---

### Post by Scorry on 2011-05-05
> **grizzler said:**
> Then open Firefox' Preferences window on the Application tab and enter **mailto** in the search field. Make sure the action set is to use Thunderbird.
Thank you. Worked for me.

---

