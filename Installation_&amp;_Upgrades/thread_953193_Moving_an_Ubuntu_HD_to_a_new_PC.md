---
title: "Moving an Ubuntu HD to a new PC"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by Fantasysage on 2008-10-19
Howdy guys. I usually don't need to ask questions here because of my roommate's proficiency in Linux. However due to the possible ramifications of what I am asking, I must come here for some help.

My current setup:

Old ('04) HP with Ubuntu 8.04 installed on one HD and Windows XP SP2 installed on the other HD. One HD is 300gigs (XP) while the other is 320 (ubuntu)

New Rig:

[New PC:]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4138011&Sku=SYXS-DG-038800") The Crsysis PC offered by tiger direct. Comes with XP Pro installed on its one 250 gig sata HD.

I want to pull the ubuntu HD out of my current PC and put it into the new PC. I know that asking to keep the install on the drive is a little insane, so i am more then happy to nuke the drive on the current pc and install it as a formatted drive on the new PC. My concern is with Grub on the original PC which I still want to use. And if the HD will cause issues on the new PC somehow.

My largest concern really is that the new PC comes with Windows XP PRO, but I do not believe a XP disk. If you guys can help me out or assuage my fears here it would be much appreciated.

For the record I am an amateur Ubuntu user for around 1 year now. I love the platform but at the moment I have a pretty rudimentary knowledge of how the ins and outs work. However my friend is highly proficient an will be helping me out, so don't hold back with the complicated solutions.

Thanks!

---

### Post by cariboo on 2008-10-20
You can just put your hard drive with Ubuntu on it in your new computer with out any problems, you will just have to reinstall grub. HAve a look at his howto:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If I remember correctly hp has a utility to create backup DVD of the restore partition, just in case.

Jim

---

### Post by Fantasysage on 2008-10-20
Well I do have the recovery DVD for the HP one. I would rather not do a full reinstall unless **** really went south however.

Also, are you sure I can really just pop the old (unformatted, w/ data on it) ubuntu HD from the old pc into the new computer, put in a live cd, install grub and be good-to-go? That would be SWEET.

---

### Post by Fantasysage on 2008-10-20
I don't know if this is kosher here but ill color this a bump.

SO should I be good putting the non-formatted ubuntu HD in and installing grub via a live CD. The instructions that I was linked too looks like it was for 1 HDD only. How would I do it for two hdd's?


Thanks!

---

### Post by Arfdaddy on 2008-10-27
If you're still looking for a way to do what you're contemplating, I've done it successfully, and I'll be happy to tell you how.  It's a bit of a booger, though, and I'd like to know that you actually still want to try it before I make the effort to collect all my info and write it down.

Here's what I think you want to do:

[LIST]
[*]Install your existing Ubuntu disk in your friends XP machine;
[*]Make Ubuntu bootable;
[*]Refrain from doing too much to the XP disk; and
[*]Leave the system in a state that makes it easy for your friend to use it his way, while still making it possible to use it your way.
[/LIST]

Is that right?

Here's what I've worked out:

My machine boots from the XP boot loader, and displays two options - Boot XP, and go to a grub menu where the Linux entries are bootable.  If you do nothing, you go to grub and boot its default system; if you select Windows, you boot to XP.  Naturally, it's easy to make XP be the default.

If that'll work for you, say so, and I'll start putting it together.

---

