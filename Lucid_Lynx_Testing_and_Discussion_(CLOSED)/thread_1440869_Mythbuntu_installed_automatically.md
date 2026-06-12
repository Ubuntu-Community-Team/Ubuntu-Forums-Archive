---
title: "Mythbuntu installed automatically?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by serosis on 2010-03-28
I did a clean install then hit the update manager, 404 files to upgrade cool. Leave it to itself and  I went to do other things, upon the restart I notice the boot screen change to "MYTHBuntu" I thought, "strange". When I get into it all I have is a taskbar at the top and a simple clock showing military time.

Seriously what... the... @$#$.

Is Linux trying to do its best to alienate me?

Is this some cruel joke just to waste my time?

Well anyways I'm on my way to reinstall yet again but this time I'll look through the update manager before I hit "Apply".

EDIT:

Running Update Manager again and I didn't find any reference to "MythBuntu".
Well the majority of it is Greek to me but I'm gonna go ahead and update.
If it happens again I'm just gonna keep to Windows till it gets fixed.

---

### Post by splicerr on 2010-03-28
I just did an update, and indeed some mythbuntu stuff got pulled in, along with some xfce stuff I don't need. Looks like somebody #@$& up!  I just used synaptic to get rid off all the unnecessary junk.

---

### Post by serosis on 2010-03-28
> **splicerr said:**
> I just did an update, and indeed some mythbuntu stuff got pulled in, along with some xfce stuff I don't need. Looks like somebody #@$& up!  I just used synaptic to get rid off all the unnecessary junk.

What did you do to get rid of MythBuntu?

---

### Post by splicerr on 2010-03-28
I used synaptic. It's got a nice history log, so you can exactly see what got installed and what got upgraded at what date and time. I just went through the list of newly installed packages from my last update and marked them for complete removal.

---

### Post by Menthu_Rae on 2010-03-28
To fix this, CTRL+ALT+F* to another TTY.

```
sudo apt-get remove --purge mythbuntu-default-settings mythbuntu-gdm-theme 
sudo reboot now

```

Now everything will be fixed!
Wow, someone screwed up good... My VM install of Lucid is now toast since I can't seem to CTRL+ALT+F* to a TTY :cry:

**EDIT:** I can get to a TTY by USB-attaching my Keyboard, hehe. Now to try to fix it ^_^
**EDIT2:** Yay! Fixed it.

---

### Post by RichardRicardo on 2010-03-28
Whatever this was got me as well. Weird thing was, I was actually googling mythbuntu while I was updating. 

I was about to go get my tinfoil hat out of the closet. Time to synaptic.

Edit:

This bug: [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-live-autostart/+bug/550088]("https://bugs.launchpad.net/ubuntu/+source/mythbuntu-live-autostart/+bug/550088") looks familiar

I also just opened up synaptic and marked the two mythbuntu packages for complete removal.

---

### Post by Arand on 2010-03-28
[https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237](https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237) is the relevant bug for this issue.

Instructions for recovery are on the report:
> Updated plymouth package with corrected recommends is on the line.

***For anyone hit by this bug you will need to manually install the package:
plymouth-theme-ubuntu-text

And then remove these packages:
lubuntu-plymouth-theme
mythbuntu-default-settings

***If you are stuck with a black desktop after boot:
Switch over to a terminal via CTRL+ALT+F2

Login and run the commands:
sudo aptitude remove mythbuntu-default-settings
sudo aptitude install plymouth-theme-ubuntu-text
   (above command will also auto-remove several xfce-related packages)

and finally reboot.
- Arand

---

### Post by zoomy942 on 2010-03-28
i didnt get hit with this bug.  just only see  plymouth on shutdown.  on boot up, it stays black until the login screen.  

should i reinstall the plymouth-theme-ubuntu-text?

---

### Post by Zilioum on 2010-03-29
Yesterday the update manager of my notebook that runs Ubuntu 10.04 beta told me that there where some updates ready. I quickly looked through the proposed packages, looked like basic stuff to me. After the update I was asked to reboot my pc and thats when I realized that something went wrong. If I start from the first kernel(2.6.32-17) I get the Mythbuntu startup screen (Like the 10.04 one but with Mythbuntu instead of Ubuntu). Then I get a black screen, with a black mouse pointer I can move around and a grey panel on top which displays the time on the right. I read that Mythbuntu has just released their 10.04 beta, so I supposed I somehow got the wrong version of Ubuntu when updating.
Any ideas what happened in details? Will removing Mythubunt fix this?

---

### Post by 23meg on 2010-03-29
I've merged your thread into a recent one on the same issue. Please do a forum search before starting new threads.

---

### Post by Zilioum on 2010-03-29
Sorry, googled it a lot but forgot to look in the forums itself :oops: I'll try the fix.

---

### Post by Zilioum on 2010-03-29
Fixed it, thanks.

---

### Post by k3pp0 on 2010-03-29
Got the same problem during an update yesterday, every got fixed except for network manager tray icon, seems broken.
I'll se if it is related or not.
Thanks for the fix.

Cheers.

---

### Post by Zilioum on 2010-03-31
At least this bug put a nice "WTF!?" expression on our faces ;)

---

