---
title: "Ubuntu 23.04 ZFS now requires encryption?"
date: 2023-08-24
forum: Installation &amp; Upgrades
---

### Post by techguy378 on 2023-08-24
I tried to install Ubuntu 23.04 on ZFS today with the new flutter based installer. For some reason selecting ZFS suddenly requires an encryption key, even if I don't check the encryption option in the Advanced Options. I don't want full disk encryption, I just want ZFS. Ubuntu has never required encryption when using ZFS before. Is this a bug? How do I install Ubuntu to ZFS without encryption?

---

### Post by #&amp;thj^% on 2023-08-24
My XFCE4 Lunar did not require encryption.
It's going on a year since I installed though.
I'm going to DL Xubuntu now and see.
"I'll be back"
EDIT:Xubuntu 23.04-23.10  encryption offered but not required.
That's one option for your non encrypted ZFS

---

### Post by techguy378 on 2023-08-25
> **1fallen said:**
> My XFCE4 Lunar did not require encryption.
It's going on a year since I installed though.
I'm going to DL Xubuntu now and see.
"I'll be back"
EDIT:Xubuntu 23.04-23.10  encryption offered but not required.
That's one option for your non encrypted ZFS

I selected the Erase Disk option. Under Advanced Options I only selected ZFS. I did not select the LUKS encryption option. After I clicked Next I was prompted to enter and confirm an encryption key. The Next option was grayed out until I entered an encryption key. Strange thing is I'm not being prompted on boot for an encryption key. My laptop just boots straight to the desktop like normal. I'm using the Gnome installer BTW.

---

### Post by #&amp;thj^% on 2023-08-25
> **techguy378 said:**
> My laptop just boots straight to the desktop like normal. I'm using the Gnome installer BTW.
How weird, I have a saying "All's Well that ends Well"
And it was clear from your first post  "Gnome installer"
The new behavior might be a new convenience or a big pain in the rear.

---

### Post by MAFoElffen on 2023-08-27
I am confused... Why you ask? I need clarifications here from the OP...

Background: 
The "Ubuntu Gnome Project" died in mid-2017. There has not been an official "Ubuntu Gnome" Installer ISO released since that time. A current Ubuntu Gnome ISO image does not exist.

Ubuntu itself, had shifted from Gnome to the Unity UI, then back to a hybid UI, referred to as "Vanilla Gnome." 

Gnome Users, like myself, stuck with Gnome, and migrated to Gnome3, through that, by installing Ubuntu, then installing Gnome Sessions.

So I am confused by "which" installer version and release you are referring to. Also, please note in a post where and when you downloaded that specific ISO image. That is important.

I downloaded the Lunar "Traditional" Installer image last night after i got home from work, tested and installed with ZFS, and it offered both ZFS, and ZFS with Encrytption...

Since it did... and everything tested successfully, I could not recreate your problem,

That's what I do when I support someone. Try to recreate the problem, to confirm it, and find a work-around to resolve it. I don't try to guess what might be wrong. I couldn't do this for you this time.

So, yes, that brings up questions on how to recreate your issue.

---

### Post by #&amp;thj^% on 2023-08-27
> **MAFoElffen said:**
> I am confused... Why you ask? I need clarifications here from the OP...
So, yes, that brings up questions on how to recreate your issue.
That threw me for a loop as well MAFoElffen but the OP had this in his first post.
> I tried to install Ubuntu 23.04 on ZFS today with the new _flutter based installer._ For some reason selecting ZFS suddenly requires an encryption key

---

### Post by #&amp;thj^% on 2023-08-27
> **1fallen said:**
> That threw me for a loop as well MAFoElffen but the OP had this in his first post.
Then went on to say, they did not need to enter any passphrase.
EDIT: That's after the install and first bootup.

---

### Post by MAFoElffen on 2023-08-27
But I just got through testing the 23.04 Snap ubiquity-desktop-installer image with the flutter UI (new installer)... Less than 20 minutes ago. The canned ZFS installer script is still turned off on that image(???)

On "Erase Disk", the only option it offers is LVM and LVM with Encryption. I just confirmed that from last night's image.

IDK. That is what I got.

This is why I am a bit confused.

---

### Post by #&amp;thj^% on 2023-08-27
> **MAFoElffen said:**
> But I just got through testing the 23.04 Snap ubiquity-desktop-installer image with the flutter UI (new installer)... Less than 20 minutes ago. The canned ZFS installer script is still turned off on that image(???)

On "Erase Disk", the only option it offers is LVM and LVM with Encryption. I just confirmed that from last night's image.

IDK. That is what I got.

This is why I am a bit confused.

Well when comes down to it, my money is always placed in you....
Dang now I have to see....EDIT: No I don't, I trust you implicitly.

---

