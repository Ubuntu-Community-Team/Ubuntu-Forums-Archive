---
title: "Installer always fails at the same place"
date: 2004-12-31
forum: Installation &amp; Upgrades
---

### Post by massivefoot on 2004-12-31
Ok, I'm new her and I'm trying to install Ubuntu. However, when I get to the 'Installing Base System' stage, the installer always fails at the same place.

At just after 20% complete I get an error message saying that 'debootstrap' exited with an error (return value 1).

I have search for previous topic on this issue, and the only advice I could find on them was to start the install either in expert mode or using the parameters 'linux noapic nolapic'. Unfortunately, none of these work.

The CD I am using was from a magazine cover, everything else seems to work ok so I assume there is no problem with the CD.

Can anybody help!? 8-[

---

### Post by hardcandy on 2004-12-31
If you can, I recommend downloading, sum checking, and burning your installation cd's. How old is the cd, ie is the version fairly new? Are there any scratches? A lot of things could be affecting it.

---

### Post by az on 2004-12-31
Does CTRL-Alt-F3 show any relevant error messages?

---

### Post by eldrich_rebello on 2004-12-31
is your cd rom drive/dvd drive working allright/.?i had a similar problem and i know it's because of using a ****$$$$ $$ cd drive.try it on a guinea pig's pc.

---

### Post by Rhodan on 2004-12-31
[QUOTE=eldrich_rebello]is your cd rom drive/dvd drive working allright/.?i had a similar problem and i know it's because of using a ****$$$$ $$ cd drive.try it on a guinea pig's pc.[/QUOTE]

Yeah I had a problem with the installer, when it got to the kernel installation stage it would say it couldn't find the kernel file. Turned out Ubuntu doesn't like my new NEC DVD writer (which works perfectly with other distro's/windows), so I had to use an old cd-rom drive to install it.

---

### Post by Mira on 2004-12-31
My first install disc was no succes....always failed at the same place, like yours, but I don't remember where anymore. Doesn't matter where that was because I burned another, this time I used disc-at-once instead of track-at-once and selected the the lowest speed, in this case 4x, instead of anything faster. Then I took a shower and when I was done I had a fine CD which installed all the way.

Some ISO's just seem to be harder to burn than others...it happens.

---

### Post by massivefoot on 2004-12-31
[QUOTE=Mira]My first install disc was no succes....always failed at the same place, like yours, but I don't remember where anymore. Doesn't matter where that was because I burned another, this time I used disc-at-once instead of track-at-once and selected the the lowest speed, in this case 4x, instead of anything faster. Then I took a shower and when I was done I had a fine CD which installed all the way.

Some ISO's just seem to be harder to burn than others...it happens.[/QUOTE]
 Right guys, thanks for that, I'm downloading the ISO's right now, I'll post again to tell you how it goes...

---

### Post by massivefoot on 2004-12-31
I've made another install CD from the ISO from the site. The installer still fails at the same place with the same error message so I can only assume that this is nothing to do with an error in writing the CD.

 :confused: 

Any suggestions would be very much appreciated...

---

### Post by eldrich_rebello on 2005-01-02
have you tried the cd on anyone else's pc?
try CTRL-Alt-F3 during the install,when it fails..post what you get.

---

### Post by DigitalCubano on 2005-01-05
[QUOTE=eldrich_rebello]have you tried the cd on anyone else's pc?
try CTRL-Alt-F3 during the install,when it fails..post what you get.[/QUOTE]
 I know this probably won't help you, but I have had the same problem OVER and OVER with 4 different CDs on 3 different computers.  I go to the base install part and it quits right around 80%...just enough to get my hopes up.  Anyhow, when I use the tool provided in the menu to check if the cd has been corrupted, I get an affirmative every time.  It's strange to me that I have no problem burning a Fedora, Knoppix or Mandrake iso but every one of my Ubunto isos are corrupted.  I also tried ordering the disc twice and it has yet to pop up in my snailmailbox.

At least your post confirmed that I wasn't doing anything wrong.  Screw Ubuntu, it's back to Fedora for me...

---

### Post by wallijonn on 2005-01-05
what type of system do you have? motherboard, cpu processor, mem, disk drives, cdrom drives.

Are you overclocking?

You may neet to run memtest to verify your memory subsystem. make sure that usb is disabled in the BIOS before running memtest86.

---

### Post by it_clumps! on 2005-01-09
go to 
[http://ubuntuforums.org/showthread.php?p=46207#post46207](http://ubuntuforums.org/showthread.php?p=46207#post46207)

I had the same problem and now the installation doesn't stop

---

### Post by perriko on 2005-01-13
Ditto for me ... 3 CD (deliverd by Ubuntu in the fancy cd jackets no less) 4 different machines - bust.
The live CDs work, but the install doesn't .

Back to Fedora - ahhh! :-)

---

