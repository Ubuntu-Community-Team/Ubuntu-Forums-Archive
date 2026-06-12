---
title: "Problems booting Ubuntu live CD"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by claus_chr on 2007-01-05
I'm having problems booting from the Ububtu 6.10 live CD. My system is a

HP Pavivion a708.dk
AMD Athlon64 3200+, 2.21 GHz
512 MB RAM
NVidia GeForce FX5200

I have tried both the 64 bit and the 32 bit versions without any luck. I have tried disabeling ACPI as described [here]("http://help.ubuntu.com/community/Installation/32bitonAMD64") and also "mem=512m", but that didn't seem to make any difference.

I first downloaded the 64 bit version, checked the MD5 sum and burned the iso. When that didn't work, I took the 64 bit iso from the Linux Format DVD (january issue), checked the MD5 sum, and this time burned the CD ROM at low speed (4x), but the result was exactly the same: The boot process reached the splash screen (which was displayed in black and gray) and the progress bar neared the end when the screen was filled with a lot of error messages (the last ones from squashfs) followed by the line "User not known to the underlying authentication module" repeated 10 times.

With the 32 bit version I get a normal, correctly drawn splashscreen, but after bouncing back and forth a couple of times, the progress bar stops in the beginning of the line and nothing happens. When I tried to use the procedure described by [Morkalin]("http://www.ubuntuforums.org/showthread.php?t=331765") I saw a list of errors similar to what I got from the 64 bit version. The last 3 lines were:

[17179578.260000] SQUASHFS error: zlib_fs returned unexpected result 0xfffffffb
[17179578.264000] SQUASHFS error: Unable to read fragment cache block [3278f6ff]
[17179578.264000] SQUASHFS error: Unable to read page, block 3278f6ff, size d009

I have had similar problems before with other Linux distributions; I did manage to install Suse 10.0 a while ago, and recently also Suse Enterprise Desktop 10. Oddly, I actually booted right into Ubuntu 6.10 (32 bit version) the first time I tried, but every subsequent attempt has failed.

Any help will be greatly appreciated

---

### Post by Sef on 2007-01-05
1) Did you do an md5sum after you downloaded the iso? 

2) Don't burn at more than 4x.  Faster may corrupt the download.

3) Stick with 32-bit for now.  Not all apps can run on 64-bit easily, if at all.

---

### Post by claus_chr on 2007-01-05
I did check the md5 sum on the 64 bit iso's - both the one I downloaded and the one I got from the Linux Format DVD. The first CD was burned at full speed, the second at 4x; it didn't seem to make any difference.

As for the 32 bit version, I got that from the Linux Format DVD. It booted correctly once, so I don't suppose there could be anything wrong with the DVD.

I will take Your advice and use the 32 bit version, if I can just find out how to install it.

---

### Post by Sef on 2007-01-05
> [17179578.260000] SQUASHFS error: zlib_fs returned unexpected result 0xfffffffb
[17179578.264000] SQUASHFS error: Unable to read fragment cache block [3278f6ff]
[17179578.264000] SQUASHFS error: Unable to read page, block 3278f6ff, size d009 

I wonder if your hard drive has some bad blocks on it.  

Update: Been doing some checking, could be your DVD drive is bad.  Have you tried to clean it.

Have you checked the CD?  There is an option to do that on the disk.

Could be bad ram too.   Run memtest.  It's on the cd, if i remember correctly.  You should let it run for about 10 times as sometimes it can pick up problems only after running for a while.

---

### Post by tboyce on 2007-03-02
I have a Z555.  I have used the live CD on three other machines without a problem.  I am getting the same set of errors.  Any other thoughts?  The drive has been fine for other software.

---

