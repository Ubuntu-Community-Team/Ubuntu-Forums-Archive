---
title: "Thunderbird 3 - Can't get it to open HTTP links."
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-21
It "should" just be "Preferred Applications", but apparently there's something new in TB3 - see attachment.

I have given up trying to figure out how to get a URL in an email to open FF...

Help!

---

### Post by Owen.C93 on 2010-03-21
Right click-open link in browser.....does that work? Make sure the e-mail isn't protected and download all content.

It works perfect for me in lucid.

---

### Post by collinp on 2010-03-21
This is a known problem. See [this Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/526290") and [this Ubuntu Forums thread]("http://ubuntuforums.org/showthread.php?t=1355078").

---

### Post by wilee-nilee on 2010-03-21
When it installs it will ask you where you want to open links, I just go to usr/bin/firefox

You can go into the about config of thunderbird and set it there but I'm not sure how.

---

### Post by emarkay on 2010-03-21
Awww, Come on! (As the whiney kid moans...)

Nothing in all these posts and links was directly the solution.  I had to figure out the following:

"Thunderbird-gnome-support" wasn't installed.
(Now I know to do this in the future)
But installing it does nothing, until you reinstall Thunderbird3!
(Luckily doing so did not overwrite or remove existing configurations!)

Now it works.

---

### Post by cariboo on 2010-03-21
You can set how Thunderbird handles links and attachments, by going to Edit->Preferences->Attachments. See screen-shot.

---

### Post by emarkay on 2010-03-21
> **cariboo907 said:**
> You can set how Thunderbird handles links and attachments, by going to Edit->Preferences->Attachments. See screen-shot.


Not here...  
But the above info did get my links working - this seems like this could be another variation on the main bug...

---

### Post by lonniehenry on 2010-03-21
emarkay - the choices will appear when you first try to open the link types. You will get to choose the different types when needed.

---

### Post by cgarvey on 2010-04-14
> **emarkay said:**
> "Thunderbird-gnome-support" wasn't installed.
(Now I know to do this in the future)
But installing it does nothing, until you reinstall Thunderbird3!
(Luckily doing so did not overwrite or remove existing configurations!)


That worked for me, thanks! Much simpler than the other fixes (involving the advanced config editor), and a whole lot more helpful than the "it should..." type posts!

Thanks for the tip!

---

### Post by thordekovbuur on 2010-04-19
Worked for me as well and I didn't have to reinstall TB3. After thunderbird-gnome-support was installed, TB3 asked me if it should be used for mail/new/feed as standard. That was all.

---

### Post by wfp on 2010-04-19
> **emarkay said:**
> Awww, Come on! (As the whiney kid moans...)

Nothing in all these posts and links was directly the solution.  I had to figure out the following:

"Thunderbird-gnome-support" wasn't installed.
(Now I know to do this in the future)
But installing it does nothing, until you reinstall Thunderbird3!
(Luckily doing so did not overwrite or remove existing configurations!)

Now it works.


Thanks worked here also. Did not have to reinstall Thunderbird.

---

