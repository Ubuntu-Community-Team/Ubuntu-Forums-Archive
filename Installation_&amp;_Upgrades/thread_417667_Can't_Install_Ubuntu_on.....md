---
title: "Can't Install Ubuntu on...."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by mburt on 2007-04-21
Alright. I was planning to get a better computer and install Linux on it first, but then I said hey: If I mess it up, I'm screwed. So now I have an older Toshiba P2.
I successfully burned the iso file as a cd image, and that's all fine.
It just won't boot.
It shows a blank line, flashing:
_
I don't think it reads CDs properly as boot disks.

edit// is there a boot disk I need or something? It won't install via cd

Thanks,
Mike

---

### Post by old_geekster on 2007-04-21
You should enter your BIOS and set the boot order to boot from the CD/DVD.  This should solve your problem.

I'm not certain which key you should press, but one of these "F1, F2, F10, OR DEL" should do the trick.

---

### Post by mburt on 2007-04-21
I know how to get into BIOS, and I changed it. But I still get a blank screen.
Is there a certain time before the boot screen should appear?

---

### Post by mburt on 2007-04-21
Common' guys. I really need this, it's late and I've spent the entire day at it.
Is there a way to set up Ubuntu without using the CD? Will making it a slave on another computer and loading the install files on the drive load it when put in the other computer?

---

### Post by mburt on 2007-04-22
Bump...

---

### Post by qpieus on 2007-04-22
Is the cd md5 sum good? If you have a bad cd it may not boot right. Also, what image did you download - the desktop or the alternate install? For old computers, the alternate install may work better.

---

### Post by mburt on 2007-04-22
How do you know if the md5 sum is good? And I did download the Desktop version... Maybe I should try the alternate. But I'm on dial-up and had a friend do the other one...

I think my computer is really messed up now though.
I formatted the hd on another comp running it as a slave, and now when I put it back in my other pc it doesn't even read the drive. I opened BIOS and there's no primary master or slave, only a secondary master which is the cd rom drive.
Confused...
Thanks for any help

---

### Post by qpieus on 2007-04-22
In a terminal, go to wherever the downloaded iso file is and type:

md5sum *iso filename*

It will return a long string of numbers and letters - that's the md5 sum.
Next go to whatever website you downloaded the image file from and there should be a link to a file called md5sums, or something close to that. That file contains the md5 sum of the original image file. Compare your sum to the original file's sum.

Also, if you boot the live cd, at the selection screen you should see a choice that says "check cd for defects" or something similar. Choose that to check the cd you used to install ubuntu.

---

