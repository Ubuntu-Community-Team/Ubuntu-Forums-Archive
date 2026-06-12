---
title: "USB Drive Access Denied after Installing Ubuntu"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by sdafsdf on 2014-03-25
Hello, I installed ubuntu last night using an 8 gb usb drive, as my computer's disk drive doesn't work. Now when I attempt to open and modify my usb on Windows, access to it is denied. I would really prefer not having to buy another one just because I can't access it like a normal external drive...

Here's a screenshot just in case: [ATTACH=CONFIG]251466[/ATTACH]

Thank you

---

### Post by polt on 2014-03-25
Can you format that USB drive?

---

### Post by sdafsdf on 2014-03-25
Yes, I am able to right click and format, but when I try to access the drive I get the error message.

---

### Post by ajgreeny on 2014-03-25
Did you actually install ubuntu to the USB drive or simply use the USB drive as a live system in order to install ubuntu to your hard drive?  It sounds as if you made a proper install to the USB which will mean that the filesystem on it is ext4 which windows is unable to read or work on in any way.

If you made a live USB it should be read by windows as the filesystem should be fat32.

More info please about exactly what you did.

---

### Post by polt on 2014-03-25
And if you do have an ext4 filesystem and can't format from Windows, you should be able to from Ubuntu.

---

### Post by sdafsdf on 2014-03-25
> **ajgreeny said:**
> Did you actually install ubuntu to the USB drive or simply use the USB drive as a live system in order to install ubuntu to your hard drive?  It sounds as if you made a proper install to the USB which will mean that the filesystem on it is ext4 which windows is unable to read or work on in any way.

If you made a live USB it should be read by windows as the filesystem should be fat32.

More info please about exactly what you did.

I simply used the usb to install Linux on my computer. Directly afterwards my USB would not work with Windows and brought the "access denied" error (still works with Ubuntu, but I need it for windows)

I actually tried another fresh USB drive on windows, and I still get the error.

---

### Post by polt on 2014-03-25
If it is happening with 2 different USB drives, that suggests that the problem is with Windows.  It's possible that something happened to your Windows installation after you installed Ubuntu.  Are you dual booting?  Or was it installed on a different computer?  In any case, you'll probably have to go elsewhere to get your Windows problems solved.  :sad:  Maybe you can reinstall it.  What do you need Windows for anyways?? :p

---

### Post by Mark Phelps on 2014-03-25
ON a hunch, I stuck in my recently-formatted-8GB-USB stick containing Mint16 installation -- and just like you, my Windows does not "like" the drive.  A partitioning utility confirmed the drive was formatted FAT32.

What I suggest you try (and NOT reinstalling Windows, BTW) is to reformat the USB stick as NTFS -- and see if Windows can use it then.

---

### Post by sdafsdf on 2014-03-26
> **Mark Phelps said:**
> ON a hunch, I stuck in my recently-formatted-8GB-USB stick containing Mint16 installation -- and just like you, my Windows does not "like" the drive.  A partitioning utility confirmed the drive was formatted FAT32.

What I suggest you try (and NOT reinstalling Windows, BTW) is to reformat the USB stick as NTFS -- and see if Windows can use it then.

Yeah, it's definitely something with those installation files that screws with the drive.

For future readers with this problem: I decided to use the Pen Drive installer to put ubuntu on the usb drive again(while formatting it within Pen Drive), and that ended up fixing the problem and giving me permissions again.

Thanks

---

