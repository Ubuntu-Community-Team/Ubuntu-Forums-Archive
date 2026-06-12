---
title: "dual boot into Ubuntu fails after upgrade"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by Fusilli Jerry on 2011-08-06
Hi Folks,

I can't boot into my Ubuntu partition after upgrading today from v9.10 to v10.0.4.3 LTS.  Details follow.

It's been a while since I last booted into my Ubuntu partition.  Over a year actually.  I booted into it today and after successfully logging in and checking things out I got the following message:

"Your Ubuntu release is not supported anymore.  You will not get any further security fixes or critical updates.  Please upgrade to a later version of Ubuntu Linux."

Then I saw the message "New Ubuntu Release 10.0.4.3 LTS is available".

I proceeded with the upgrade which took about 30 minutes.

When it was complete I was prompted to reboot.  I have a dual boot setup which I used Wubi to create back in early 2010.  When the reboot prompted me to choose between Ubuntu and Windows I chose Ubuntu.  At this point something flashes in the top left of the screen but its too fast to read.  Then the computer goes back to the beginning of the boot and in a few seconds I am prompted to choose between Ubuntu and Windows again.  

No matter how many times I choose Ubuntu it just restarts the boot and doesn't proceed.  Thankfully I can still boot into Windows XP.

I have no clue what the problem is.  The upgrade seemed to complete normally from what I saw.

One other question I have is why would it upgrade today to 10.0.4.3 LTS when the current version of Ubuntu appears to be 11.04?  I guess its possible I wrote down the wrong version number.  Does that seem right?

Please let me know if there is any other info I can provide.

---

### Post by Fusilli Jerry on 2011-08-06
Here's some more info that will hopefully be helpful.

The message shown in the upper left-hand corner of the screen during boot after selecting Ubuntu is "error: file not found".

I tried replacing the C:\wubildr with the version from D:\ubuntu\winboot but the results are the same.

There are no files in the D:\ubuntu\disks\boot\grub directory?  Is that a problem?

Many thanks for any suggestions.

---

### Post by Fusilli Jerry on 2011-08-06
Just wanted to add that I'm fine with blowing away Ubuntu and completely reinstalling using the Wubi installer if that's the easiest solution.

If that is the case, what's the simplest way to go about it?  My Windows XP "Add or Remove Programs" shows Ubuntu.  Can I just uninstall from there and then go about a clean install from scratch?

---

### Post by bcbc on 2011-08-07
Yes, the simplest way is to reinstall. Run Wubi again and it will uninstall. If instead you try and fix it and upgrade to 11.04 you'd have to go to 10.10 first and then 11.04 after that (you can only upgrade to the next release).

As to why it's not booting - not sure. I doubt anyone tested a 9.10 upgrade to 10.04.3 since 9.10 hasn't been supported since a few months prior to the 10.04.3 release (third update to the long term support release 10.04). So, while it's probably fixable... I doubt it's worth the effort.

If you have any data you want saved from the root.disk download and run [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) and point it at C:\ubuntu\disks\root.disk

Hope that helps

---

