---
title: "Critical crash when installing Ubuntu 10.10"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by kuramayoko10 on 2011-02-25
Hello guys,

You have to give me a light here... 
My friend just received its Ubuntu 10.10 CD from the mail and went right away to install it on his laptop. The CD ran fine, the installation was going as expected but when a message popped up saying "Ready whenever you are" or something like that, the computer froze.

We waited for aproximatelly an hour and the computer was still frozen. We said OK, let's try rebooting, but then comes the surprise, the computer won't boot. He lost his windows partition along with it.
The only thing we see is the black screen with the blank space character blinking at the top and nothing happens.

What should we do? Is there any way he can backup his windows files before formatting it all? He has all his college files in it :(
Is this problem in Ubuntu installation ever noticed? How can I report it back to the developers?

Thanks in advance,

---

### Post by Hedgehog1 on 2011-02-25
> **kuramayoko10 said:**
> Hello guys,
... "Ready whenever you are" or something like that, the computer froze.

We waited for aproximatelly an hour and the computer was still frozen. We said OK, let's try rebooting, but then comes the surprise, the computer won't boot. He lost his windows partition along with it.
The only thing we see is the black screen with the blank space character blinking at the top and nothing happens.


kuramayoko10,

there are two possibilities I see here:

(1) If you did not defrag the windows partition, the install was not 'hung', but was taking a (really) long time moving the data.  In this case the disk is pretty messed up.

(2) Ubuntu did install, but you are seeing the 'video driver hang' display.

Please reboot the PC using the Ubuntu CD and choose the 'try' option.  Then, menu to System >> administration >> Disk utility and look at the condition of the hard drive.

Please tell us what the disk looks like.

---

### Post by kuramayoko10 on 2011-02-27
He tried booting the cd again and starting the installation again. At this time now, he noticed that the only thing he did wrong before was to try to name his computer with capitalized letters. By correcting this, the installation finished successful.
But still we don't understand why it did get frozen, and the windows partition got deleted.

He can boot on linux now, but he lost all his files, his whole hard drive is free to use =/

---

### Post by kansasnoob on 2011-02-27
> **kuramayoko10 said:**
> He tried booting the cd again and starting the installation again. At this time now, he noticed that the only thing he did wrong before was to try to name his computer with capitalized letters. By correcting this, the installation finished successful.
But still we don't understand why it did get frozen, and the windows partition got deleted.

He can boot on linux now, but he lost all his files, his whole hard drive is free to use =/

Always read the release notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> In dual boot installs, side-by-side partitioning can be overridden by the user, resulting in data loss. After selecting the "Install alongside other operating systems" option, clicking on either the "Use entire partition" of "Use entire disc" buttons will override the side-by-side partitioning and result in a loss of data.

I fought tooth and nail to get that fixed, check post #1 and post #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I also mentioned the "no CAPS" issue there:

> NOTE: The user name must not include CAPS!

---

### Post by kansasnoob on 2011-02-27
BTW here are the bug reports:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555896](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555896)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

