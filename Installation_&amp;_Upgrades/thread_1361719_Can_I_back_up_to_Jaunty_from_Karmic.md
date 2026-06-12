---
title: "Can I back up to Jaunty from Karmic?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Mike Romain on 2009-12-22
Folks, I installed karmic and, well, nothing works.  I have a HP laptop with an AMD Turion X2 64 bit with the ATI Radeon 3400 I believe it is. 

The grub says I am running Ubuntu 9.04, kernel 2.6.28-15 however the Ubuntu help page says 'You are using Ubuntu 9.10 - the Karmic Koala' so I don't really know what's up.  Have put in all the latest updates.

The video doesn't work, takes 3-6 boots to get a stable screen, the mouse barely works, the touchpad doesn't work, the camera doesn't work, the phone camera doesn't work, etc.

I have tried too many things I think already....  I got it to sort of work but have had enough.  I think waiting for a real stable release is best and want to back up.

Can I just go back to the last stable Ubuntu which I think was Jaunty and if so how do I go about it?

Thanks.

Mike

---

### Post by Dunatotatos on 2009-12-22
Hi,

No you can't. The best (and the only, I think) way is to reinstall Ubuntu.
I hope for you that you have /home on a separated partition :p

---

### Post by Mike Romain on 2009-12-22
> **Dunatotatos said:**
> Hi,

No you can't. The best (and the only, I think) way is to reinstall Ubuntu.
I hope for you that you have /home on a separated partition :p

Please elaborate.

Karmic just plain doesn't work so reinstalling it seems pointless.

Can I move /home to another partition and move it back after a brand new install of Jaunty?  Is that what you mean?

---

### Post by raymondh on 2009-12-22
> **Mike Romain said:**
> Please elaborate.

Karmic just plain doesn't work so reinstalling it seems pointless.

Can I move /home to another partition and move it back after a brand new install of Jaunty?  Is that what you mean?

Mike,

If you have nothing in Karmic to save (assuming that all your personal files are saved elsewhere) like preferred apps, etc, then I would just re-install jaunty and build up from there.

If you already have applications/dependencies, etc, that you would like to 'import' from Karmic to jaunty when you re-install Jaunty, see this link.

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

I have not tried above-method.  Just passing on what I bookmark as "just-in-case" :)

Regards,

---

### Post by iponeverything on 2009-12-22
> **Mike Romain said:**
> Please elaborate.

Karmic just plain doesn't work so reinstalling it seems pointless.

Can I move /home to another partition and move it back after a brand new install of Jaunty?  Is that what you mean?

That should work just fine.

What I could is is tar up /home and put in on a pen drive. Add the -p option so that preserves permissions. Also use the -p when you extract it.

- What I would do is tar up /home check the tar file to make sure it is good. 

- copy /etc/passwd to thumb drive so that you remember the UID and GID of the accounts. (you might as well just back up /etc/ as there might be something in there that you want to look at later)

- Do clean install of Jaunty and create the same accounts that were on old install.

- Log in as root and move the /home to /home.new and untar backup /home that you made. 

- Fix the UID's and GID's /etc/passwd and /etc/shadow.

Then after after you reboot you should be good..

---

### Post by Dunatotatos on 2009-12-22
EDIT : I was anticipated :p

---

### Post by Mike Romain on 2009-12-22
Thanks folks, I have moved those files to a different partition and am going to try a clean new install of jaunty.

Too bad the drivers don't fire up in karmic but after messing with it for a couple weeks I have given up.  I likely made it worse even uninstalling and reinstalling things and forcing vesa for a sort of boot.  Have other things to do.

---

### Post by Mike Romain on 2009-12-23
I had decent luck moving /home back over to Jaunty with one program complaining that the permissions in /home/.dmrc aren't correct and it wants 644 and only one owner.  I will have to adjust that.

The link provided by raymondh about importing applications/dependencies was written towards upgrading I believe, it doesn't seem to work well going backward, not well at all. It killed most of the paths to lots of things like the other hard drive, the USB stick, CD/DVD, etc.

I had to reinstall Thunderbird, but it kept all the email info and Newsgroups intact.

All in all, fairly painless, thanks again.

Mike

---

