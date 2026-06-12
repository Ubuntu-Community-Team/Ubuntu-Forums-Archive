---
title: "How do I fix apturl? Lucid"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-04-17
Okay, so I told apturl to use firefox while in the getdeb website for installing apps.

Bad move, now it opens up about 10 tabs per second and I have to kill firefox to make it stop.

How do I fix this?

---

### Post by crjackson on 2010-04-17
No one knows?

---

### Post by zekopeko on 2010-04-18
> **crjackson said:**
> No one knows?

Its considered impolite to bump your own thread before a day passes.

---

### Post by Penguin Guy on 2010-04-18
It might help if you explained yourself more thoroughly.

---

### Post by lovinglinux on 2010-04-18
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Go through those steps to see if you can find the culprit and post your results.

---

### Post by crjackson on 2010-04-18
> **Penguin Guy said:**
> It might help if you explained yourself more thoroughly.

I went to the getdeb website to install a few apps I wanted.  I added the repositories and the key.

I clicked the install button on the web page.  A box popped up and asked me which application I wanted to use.  In the list it presented apturl and browse.  For some unknown reason (prolly my pain meds) I browsed to Firefox and made it the default.

It the precoded to open up browser tabs at the rate of about 10 per second.  I couldn't make it stop except to open a terminal and killall.

I should have selected apturl as my default application for web installs.

I'm trying to figure out how to either set it back to it's default where it asks which application do I want to use so I can select apturl the next time.

---

### Post by crjackson on 2010-04-18
> **lovinglinux said:**
> See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Go through those steps to see if you can find the culprit and post your results.

Reading now.

---

### Post by crjackson on 2010-04-18
> **zekopeko said:**
> Its considered impolite to bump your own thread before a day passes.

Thanks for your most helpful reply.

---

### Post by lovinglinux on 2010-04-18
> **crjackson said:**
> I should have selected apturl as my default application for web installs.

Yes. Go to "Edit >> Preferences >> Applications" and set it like the image below:

(BTW, is indeed considered impolite to bump your thread so fast. If you need a quick response, go to irc://freenode/ubuntu)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153657&stc=1&d=1271603847[/IMG]

---

### Post by phrostbyte on 2010-04-18
IMO hitting an apt:// link should just use launch apturl right away and not prompt the user to set a protocol binding. It used to do this! Perhaps this new behavior is a bug?

Now I can not really claim apt-url is a "one click install". :(

---

### Post by crjackson on 2010-04-18
> **lovinglinux said:**
> Yes. Go to "Edit >> Preferences >> Applications" and set it like the image below:

(BTW, is indeed considered impolite to bump your thread so fast. If you need a quick response, go to irc://freenode/ubuntu)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153657&stc=1&d=1271603847[/IMG]

Perfect.  Thank you VERY much!

---

### Post by crjackson on 2010-04-18
> **phrostbyte said:**
> IMO hitting an apt:// link should just use launch apturl right away and not prompt the user to set a protocol binding. :(

I agree!

---

### Post by Tank! on 2010-04-19
How can I add the 'apt' content type if it is not listed in my Applications tab in the Firefox preferences?

---

### Post by Tank! on 2010-04-20
I tried the steps outlined at [http://www.webupd8.org/2009/10/fixing-apturl-for-firefox-35-and-later.html](http://www.webupd8.org/2009/10/fixing-apturl-for-firefox-35-and-later.html)

I am still getting the same error message. I'm running Firefox 3.5.9 on Ubuntu 9.10. As this thread was posted in the Lucid section and listed as [SOLVED], should I start a new thread?

---

### Post by lovinglinux on 2010-04-20
> **Tank! said:**
> I tried the steps outlined at [http://www.webupd8.org/2009/10/fixing-apturl-for-firefox-35-and-later.html](http://www.webupd8.org/2009/10/fixing-apturl-for-firefox-35-and-later.html)

I am still getting the same error message. I'm running Firefox 3.5.9 on Ubuntu 9.10. As this thread was posted in the Lucid section and listed as [SOLVED], should I start a new thread?

What error? That one when you click an apturl link and Firefox says it can recognize the uri? Have you tried to restart Firefox?

---

### Post by Tank! on 2010-04-20
Yes, the error message reads: "Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program." I restarted Firefox a few times (completely closing all open windows and verifying in System monitor that the process was no longer running).

---

### Post by lovinglinux on 2010-04-20
> **Tank! said:**
> Yes, the error message reads: "Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program." I restarted Firefox a few times (completely closing all open windows and verifying in System monitor that the process was no longer running).

Have you tried to change the settings like post #11?

---

### Post by Tank! on 2010-04-20
Yes. There was no 'apt' content type to be selected in my Firefox preferences. This is the reason I added on to this thread.

---

### Post by lovinglinux on 2010-04-20
> **Tank! said:**
> Yes. There was no 'apt' content type to be selected in my Firefox preferences. This is the reason I added on to this thread.

I suppose you have installed apturl. So close Firefox and move the file mimeTypes.rdf from your profile to somewhere safe (you might need to restore it later), then start Firefox and try again.

---

### Post by basily on 2010-04-27
I too am having the same problem. Anyone?

---

### Post by Tank! on 2010-04-27
Hi lovignlinux, 

I did move the mimeTypes.rdf file away from my .firefox folder, but still to no avail. The issue seems to be that I cannot add 'apt' in my content type dialog bock in my firefox prefrences. 

Thanks for all your help nonetheless!

---

### Post by lovinglinux on 2010-04-27
> **Tank! said:**
> Hi lovignlinux, 

I did move the mimeTypes.rdf file away from my .firefox folder, but still to no avail. The issue seems to be that I cannot add 'apt' in my content type dialog bock in my firefox prefrences. 

Thanks for all your help nonetheless!

After deleting it, try the instructions from [http://www.webupd8.org/2009/10/fixing-apturl-for-firefox-35-and-later.html](http://www.webupd8.org/2009/10/fixing-apturl-for-firefox-35-and-later.html)

---

