---
title: "Install partitions"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-10-19
I've used Ubuntu on a spare hard drive I had and it worked fine. I now wish to dual boot with XP. I have prepared my 160GB disk as follows (numbers approximate): 1st partition 80GB, WindowsXP; second partition 13GB unformatted for Breezy; third partion 5GB Fat32; fourth partition what's left NTFS. How does that look?
Will I have the oportunity to choose the second unformatted partition for Breezy?
Anyone using GAG on a floppy to boot? Is GRUB better? :confused:

---

### Post by Herman on 2005-10-20
It looks to me like you have done a good job there so far, AllanP!

Yes, you will be given a chance to choose which partition you'd like to install Breezy on.  
There's an illustrated example install you can look at by clicking on my signature link, but since you've already partitioned yours, your install won't be the same as that. But just for reference, after 8th illustration where you pick 'manually edit partition table', you'll get a list of partitions you can choose from to install on. In the example there's only one, but yours will be a list and you'll be able to choose the right one.

I don't know much about GAG yet, but I'd just try GRUB first and use GAG if GRUB doesn't work maybe. 
I'm presently trying to make a GRUB CD, but that's not as easy as I though.
The easiest and best for most people is just to install GRUB to the master boot record. A lot of people are having trouble with GRUB, but I bet for every one that posts a problem there would be hundreds who install and don't have any problems. 
Well, that's what I think anyway, all the best with it!       (Herman).

---

### Post by AllanP on 2005-10-20
Thanks Herman

I did the install without a hitch; used GRUB and all is ok. Now I just have to de-Widows myself and learn Linux.

---

### Post by jonrkc on 2005-10-20
One thing you might want to watch out for, using GRUB, is that every time a kernel update takes place, the /etc/boot/grub/menu.lst file gets automatically changed.  So (providing the kernel version is still the same) I just make a copy of my good menu.lst file beforehand, and then after the update, I swap it back for the altered one.  Then I have the same familiar menu for booting as I'm used to.  And even if the kernel version nomenclature changed due to some relatively major upgrade, the name could just be changed manually where it exists in the /boot directory and in ../grub/menu.lst.  That would preserve the boot order that the user is familiar with and may press "enter" on unthinkingly early in the morning.  :)

I used LILO prior to GRUB and with my limited expertise I prefer GRUB as easier to handle and more forgiving.  Editing the menu.lst file is really easy, too.

Sometimes the grub-update function (or is it update-grub?) in GRUB has done unexpected things for me, but nothing that wasn't easy to undo.  As long as the conventions (hd0) for /dev/hd1, (hd1) for /dev/hd2 etc. are kept in mind, it's pretty easy to repair damage or make changes to the booting procedure using GRUB, preferably of course from a Live CD outside the actual installed operating system that needs fixing.

Good luck with the "de-Window"'ing part.  I did that when the last straw broke this particular camel's back, entered into Linux with no knowledge whatever, still don't have a whole lot, but have never for a moment regretted the experience.  For one thing the added speed of operation and true multitasking (I'd been using Win Ninety-Eight first edition) just about knocked me out of my chair!  For another, I like the looks of Linux distros on the screen.  Especially as antialiasing gets better and better!  (Sorry, antialias opponents, I respect your point of view, too.)

Microsoft makes some really good software but I just could no longer support the marketing practices with a good conscience.  Now I sleep better at night except for the noise of my upstairs neighbors.  ;)

---

### Post by Herman on 2005-10-20
Congratulations, Allanp, you just graduated into a higher level with computers ! :p 
(Have you ever read the book 'Jonathan Livingston Seagull', by Richard Bach?)
(recommended).
I'm pleased that your install went smoothly, and thanks for the feedback.
Ah..., just one thing though, when you graduated from elementary school to high school did you forget all you learned in elementary?
Or, if you take up a martial art do you forget what you learned as a lower belt when you reach black belt level? (Which, I have read, is just another new beginning).
So you don't need to 'unlearn Windows', (I mean this in a freindly way), just keep learning Linux, you'll do fine! As you progress, you just might find you can do a lot of things with Linux that you couldn't do before though.

That's all for now, all the best, AllanP! :D

---

### Post by jonrkc on 2005-10-20
[QUOTE=Herman]
So you don't need to 'unlearn Windows', (I mean this in a freindly way), just keep learning Linux, you'll do fine![/QUOTE]
That's a good point and a nice distinction.

I think that, in my case, what I had to "unlearn" was my DEPENDENCY on Windows.  I still remember quite a bit about operating under Windows and am able to help friends who still use it for one reason or another.  

I know one thing: I'll never learn enough about Linux/Unix to be anything like an expert.  Life is too short and I have to do other things like read the comics and (occasionally) try to sleep.

---

