---
title: "Dell 530 Can't Install"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by parsimony on 2008-01-18
Trying to instal Ubuntu - but after initial screen I just get a flashing cursor - I've tried safe mode but still a flashing cursor.

Surely this should be easy - Dell use this as one of their Ubuntu machines.

If Ubuntu is ever going to get more popular it really needs to sort these installation issues out.

Dimension 530 Desktop with 8600GT

Many thanks for help.

---

### Post by Sef on 2008-01-18
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Make sure the download is good.)

2) Did you burn the iso at 4x or less? (Faster may corrupt the burn.)

3) Did you run 'Check Disk for Defects'? (Make sure the disk is good.)

---

### Post by parsimony on 2008-01-18
Thanks for your reply, Sef.

I didn't do 1, 2 but I just tried 3 - and again I get a flashing cursor top left of my screen.

Isn't there a log or something or text install?

What is it actually doing or trying to do at this stage?

I can always try downloading again.

I have bee trying Ubuntu/Linux for years on and off and always have problems - 2 steps forward, 2 steps back.

In the old days it took ages to get the ubiquitous Speedtouch modem going - now I have ethernet so that's gone - then I think there were SATA problems - now I'm guessing its something to do with the graphics?

Any help appreciated - even though I'm moaning (frustration).

Also, I've just re downloaded again and also installed a Windows md5sum program - I Think it comes up with this d2334dbba7313e9abc8c7c072d2af09c - good or bad?

Why not include this on the cd? (Note to installation team) - and on your web pages (note to webmaster)

Shall I reburn at 4X (seems primitive)

---

### Post by Partyboi2 on 2008-01-18
Always good to burn the iso at a very low speed like x4 or lower. Hopefully that might work. If not have you thought of trying the alternate cd? Its a text base installer and pretty easy to use.
[Alternate cd]("http://releases.ubuntu.com/releases/7.10/")

---

### Post by parsimony on 2008-01-18
Thanks

Tried the alternate CD - did the checksum - burnt at lowest my sw would allow x7

Still flashing cursor at top right after initial install menu

Surely it can't be that difficult - isn't there a log, or step-bystep method and then we could find out where its failing?

---

### Post by Partyboi2 on 2008-01-18
When you are at the main menu press F6 to edit boot options
Change ```
splash
``` to ```
nosplash
``` and delete ```
quiet
```. Thejn press enter to boot This should tell you where the system is hanging.

---

### Post by parsimony on 2008-01-18
Hi

I have 2 disks

I managed to install it on my 2nd hard disk (I didn't want to muck up my existing Windows on disk1)

I have no idea how I managed to get the install to work in the end - maybe it was some kind of timing issue - I clicked on one of the options and off it went after talking about probing (I have a USB hub)

I now have a problem with booting - it says Error 17 - cannot mount

When I installed I put GRUB on hd1 - the second hard disk

So its trying to boot root(hd1, 0)

I didn't want my MBR on disk 1 overwritten

How do I edit GRUB to get it to boot? Thanks

---

