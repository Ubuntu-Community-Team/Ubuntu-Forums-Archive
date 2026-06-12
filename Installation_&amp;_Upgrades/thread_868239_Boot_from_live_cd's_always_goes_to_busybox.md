---
title: "Boot from live cd's always goes to busybox"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by doomslagen on 2008-07-23
](*,) I boot up the computer, then wait while the ISOLINUX thing loads. It takes me to a screen, where I enter "English" as my default language. Then, I choose to try it without changing anything on my computer. It goes to a screen where a orange bar goes back and forth across the screen. Then, it displays Busybox. I restart my computer, and choose to install it this time. Same result. I burn another CD, this time as slow as possible. I boot it again with the new CD. Same result with both options. Even when i choose the "Check CD" Option, it goes to busybox. Next, I Burn a thrid CD. Again, same result. I order a CD from Ubuntu. Same Result. I try the Alternate CD. It starts, then while installing the base system, first displays that "eject" is corrupt, then that it cant finish installing the base system. Does this for both Alternate cds that i burn...is THAT enough info for you? To answer the hardware specs, I dont know what hardware my computer has. Nothing has a label. Oh and did i mention that this happened for both of my computers, but when i went over a friends house and tried the live cd on his computer, it worked there? Oh and please limit the geek talk...i am still fairly new to linux, but i do know my basics. Also, I never had problems like this with previous versions of Ubuntu. They worked just fine.

---

### Post by R.C. on 2008-07-23
> **doomslagen said:**
> ](*,) I am frustrated with this problem. No matter what live CD i use, no matter what option i pick, i ALWAYS end up at the busybox thing...what do i do?

I wish I could tell you, doomslagen. I'm right there with you: ALWAYS Busybox.

I'd be more comfortable if someone could at least explain why it's happening, even if they can't suggest a solution for it!

---

### Post by Tux Aubrey on 2008-07-24
> what do i do?

1. Provide more information.  Hardware - cpu, RAM, etc.  How did you burn the CD?  Did you check it?  Do other distros boot OK?  What's the busybox error message?

It does sound like a fundamental hardware issue but if, say, you have 256Mb of ram, you may need the alternate CD rather than the live one.

2. Don't post follow-up requests on irrelevant threads (at least not without an actual link back to this one!)

---

### Post by kerry_s on 2008-07-24
a lot of times that happens when you burn the iso to fast, you want to burn slow 4x if you can.

---

### Post by oceallaighm on 2008-07-24
Thought that this may be of some help.

Link to earlier post that I had.

[http://ubuntuforums.org/showthread.php?t=836160](http://ubuntuforums.org/showthread.php?t=836160)

---

### Post by ribico on 2008-07-24
I solved adding all_generic_ide kernel option at boot as described by avtolle at the following link 
[http://ubuntuforums.org/showthread.php?t=866882&highlight=busybox](http://ubuntuforums.org/showthread.php?t=866882&highlight=busybox)

ciao
- gab

---

### Post by ribico on 2008-07-25
please remember to remove that option from /boot/grub/menu.lst file after installation.
My HDDs were really slow with that option enabled, less than 5MB/s of transfer rate.

ciao
- gab

---

