---
title: "About to give up - Ubuntu Installer window keeps closing..."
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by mobilehavoc on 2006-08-23
So I decided to uninstall Vista Beta 2 from my non-Windows XP partition and give Ubuntu a test spin.

Stuck the CD in, standard mode failed to load due to some video problem so I used the "Safe video mode" which loaded up fine.

Launced Install from the desktop and went through the steps until I got to the Partitioning part.

I have 1 250GB HD in my system...1st partition is a OEM restore, 2nd partition is XP-NTFS, 3rd partition is for alternate OS-NTFS, 4th partition is for alternate OS-NTFS.

I selected to mount root on 3rd parition and swap on 4th partition with "Reformat" checked for both. Went to the next screen and it summarized what it was about to do so I said "Forward" and a little window with a progress bar came up..

Some text flashed by about formatting or partitioning and then the "Please wait..." at the top of the progress bar changed to "Installing system" after which in about 1 second the thing just dissapeared.

Very bizzarre - I can't find anything on here off hand that can explain it. I've already run a checksum check of the CD I burnt using the ISO and got no errors.

The thing loads up beautifully but just doesn't want to install!!!!!

It's 2AM and I've been up the last 2 hours trying to get it work without success - could really use your help making this happen.

My system is a P4-3.2Ghz, 2GB of DDR RAM, 250GB HD (4 partitions as described), ATI X800 XL 256MB PCIE, SB Audigy..and I think that's really about it.

Again I'm a Linux noob but I learn fast and want to so please help me out! :confused: :confused:

---

### Post by Scythe!? on 2006-08-23
Try the alternative cd installer, this is a text mode based install cd and this fixes many problems, but the Live CD worked for me first time.

---

### Post by mobilehavoc on 2006-08-23
Ok, well I downloaded the alternate install CD but I also downloaded Fedora Core 6 Test 2 so I might give that a shot before I go through the Ubuntu alternate install. 3 hours of dealing with Ubuntu install hell has turned me off it for a bit - need some time to recuperate.

---

### Post by mobilehavoc on 2006-08-23
Alternate CD installer worked! I actually gave Ubuntu another chance before trying Fedora and it worked great.

I also installed XGL/Compiz on it within 10 mins. Pretty impressive for a *nix noob. 

Couple of bugs I need to look into in that for example my shutdown menu (top right corner button) no longer has any buttons for Shutdown or Restart...they disseapeard. All i have is a huge Hibernate button in their place (along with the standby, lock, logout).

Also when I hit logout it logs me out but then seems to freeze with nothing on the screen requiring a hard-reboot.

Weird things indeed.

---

### Post by nalmeth on 2006-08-23
Yeah that stuff sounds weird.. I'm glad you were able to install, I was going to mention that you may have too many partitions, but it appears not to be the case.

The live installer was a new thing for the last ubuntu release, and it has shown buginess. Here's hoping things will be better in Edgy.

Again, weird stuff you're going thru, perhaps has something to do with your vid card, or the drivers

---

