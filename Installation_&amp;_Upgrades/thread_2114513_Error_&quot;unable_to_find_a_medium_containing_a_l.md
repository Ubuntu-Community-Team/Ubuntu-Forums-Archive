---
title: "Error &quot;unable to find a medium containing a live file system&quot;"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by abhishekkjain on 2013-02-10
I have created a thread here.
ubuntuforums.org/showthread.php?p=12502175#post12502175

Assuming I can install ubuntu 10.04 on 256 mb ram (read last year) I tried again but failed to install it.

"unable to find a medium containing a live file system"

I got the same issue when I tried Linux approx 1 n half year ago on same system. It was 10.04 and it worked on my friend's PC and my brother's PC.

I want to use ubuntu. Please help me with this.


I have removed my USB mouse and tried installing but failed.

---

### Post by sanderj on 2013-02-10
> **abhishekkjain said:**
> I have created a thread here.
ubuntuforums.org/showthread.php?p=12502175#post12502175

Assuming I can install ubuntu 10.04 on 256 mb ram (read last year) I tried again but failed to install it.



As explained on [http://ubuntuforums.org/showthread.php?p=12502175](http://ubuntuforums.org/showthread.php?p=12502175) , you can't run Ubuntu on a 256 MB RAM system.

---

### Post by Lucius Ferus on 2013-02-10
Xubuntu supposedly does and is basically the same.

---

### Post by TheFu on 2013-02-10
On a system this small, I think you'd be much happier using a minimal Linux like **TinyCore.** Tinycore runs on extremely limited setups like yours.

To provide any real help, we need more information on the failures.
* clear description of every part that works and where it fails
* log files
* exact chips used for the system components or specific model + vendor information.

Did you get passed the BIOS screen? Grub boot screen? Ubuntu splash screen? Language selection screen?

Most of the time, we strongly suggest running a LiveCD version of the OS before installing. If this works, that means that your hardware is supported.

I think that error is related to storage access.  Are you using a DVD, CDROM, or USB installation?  USB didn't support boot many years ago, so that could be an issue. Also, different optical devices are known to have issues, so the make/model of the drive could be the issue.  Some flash drives don't seem to work with some USB controllers too.

Is your PC exactly the same as the other two that you are comparing it?

---

### Post by abhishekkjain on 2013-02-11
> **TheFu said:**
> On a system this small, I think you'd be much happier using a minimal Linux like **TinyCore.** Tinycore runs on extremely limited setups like yours.

To provide any real help, we need more information on the failures.
* clear description of every part that works and where it fails
* log files
* exact chips used for the system components or specific model + vendor information.

Did you get passed the BIOS screen? Grub boot screen? Ubuntu splash screen? Language selection screen?

Most of the time, we strongly suggest running a LiveCD version of the OS before installing. If this works, that means that your hardware is supported.

I think that error is related to storage access.  Are you using a DVD, CDROM, or USB installation?  USB didn't support boot many years ago, so that could be an issue. Also, different optical devices are known to have issues, so the make/model of the drive could be the issue.  Some flash drives don't seem to work with some USB controllers too.

Is your PC exactly the same as the other two that you are comparing it?

Hmmm as told on other thread I now understand that it is not possible.

BTW I could not even reach thay live page/ installation page.

It copies the files. (sound of dvd reader indicates that) and then I get this error.
No worries will check this new os. BTW other GUI based linux to work on my OS?

I am having NTFS n Windows installed. Also found that cmos cell holder is broken.
:p

will it affect installation?

---

### Post by TheFu on 2013-02-11
> **abhishekkjain said:**
> Hmmm as told on other thread I now understand that it is not possible.

BTW I could not even reach thay live page/ installation page.

It copies the files. (sound of dvd reader indicates that) and then I get this error.
No worries will check this new os. BTW other GUI based linux to work on my OS?

I am having NTFS n Windows installed. Also found that cmos cell holder is broken.
:p

will it affect installation?

**TinyCore** [http://www.tinycorelinux.net/](http://www.tinycorelinux.net/) is designed for older systems and absolutely runs extremely quick on current hardware - instant program launch happens inside a VM on my C2D box. TinyCore is a GUI Linux that should work on 64M of RAM systems with 50-100M of disk storage.

Just because a DVD is spinning doesn't mean anything is being copied.

Putting Windows on the machine will probably show any hardware errors that you've seen too.

Anything broken in a PC can impact everything, it just depends on the specific part.  I've seen unstable power destroy a system to the point that the GPU and power supply had to be replaced.  I don't know what a "CMOS cell" is, but if it is broken, that is not good. If it is the CMOS battery, it shouldn't be too bad, but it will be a major hassle since having the incorrect time on a computer is terrible for many, many, many reasons, including system security.

I get the feeling you don't want to spend any money. 

[LIST]
[*]For $75 where I live, a much more capable APU/MB (AMD E350) can replace your old MB/CPU.
[*]For $200, something 15x faster is available.  [http://www.pricewatch.com/gallery/motherboard_combos/core_2_duo_e8400_cpu_fan](http://www.pricewatch.com/gallery/motherboard_combos/core_2_duo_e8400_cpu_fan)
[*]Get a Raspberry-PI for $50, if you are really cheap, It runs Debian/ARM and uses very little power.
[/LIST]

---

