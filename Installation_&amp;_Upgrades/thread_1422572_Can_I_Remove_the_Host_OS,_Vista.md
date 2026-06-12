---
title: "Can I Remove the Host OS, Vista"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by JasonSilver on 2010-03-05
I installed Ubuntu from within Vista, and now that I have VirtualBox running in Ubuntu, never need to boot into Vista again. (THANK GOD!)

But since I installed Ubuntu within Vista, I wonder if it is even possible to remove Vista? 

Can someone direct me to how that might be possible, and/or a place where this has been discussed already?

Thanks so much,
Jason Silver

---

### Post by appier on 2010-03-05
I am sure there is a better way.  But, the way I have done this in the past is to back up the home folder, including the hidden folder which includes your virtual machine, to a couple of different media.  Then do a complete, fresh install, reinstalling the packages you like.  At that point, restore your home folder followed by changing the permissions.

The caveat is that I am not as experienced in Ubuntu as many of the people here, so I would get advice from more than just me before you try it.

Hope it helps!

---

### Post by theozzlives on 2010-03-05
> **appier said:**
> I am sure there is a better way.  But, the way I have done this in the past is to back up the home folder, including the hidden folder which includes your virtual machine, to a couple of different media.  Then do a complete, fresh install, reinstalling the packages you like.  At that point, restore your home folder followed by changing the permissions.

The caveat is that I am not as experienced in Ubuntu as many of the people here, so I would get advice from more than just me before you try it.

Hope it helps!

That's pretty much the only way to get out of WUBI and keep your settings.

---

### Post by JasonSilver on 2010-03-06
OK, thanks!

Now, I have a problem: I don't have a CD drive on this laptop, so the only way to get Ubuntu installed was to use Wubi through Vista.

If I format, I'll be back to where I started, except without a guest OS to download and install with.

What would happen if I just deleted the Windows folder et al?

Jason

---

### Post by MelDJ on 2010-03-06
do you have a pendrive? 
if you do try [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by JasonSilver on 2010-03-06
That might work... let me look into it.

Jason

---

### Post by JasonSilver on 2010-03-06
OK, do I just compress everything in /home/jasonsilver including all hidden files to the USB? What about software etc? 

I don't mind reinstalling the software I need-- but are all software settings in /home/jasonsilver?

Thanks!
Jason

---

