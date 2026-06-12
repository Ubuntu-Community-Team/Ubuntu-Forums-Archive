---
title: "ISO Troubles"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by sevenrechlin on 2005-11-08
Hello, I'm new to linux and (ofcourse) Ubuntu but am very interested in learning about it.  I downloaded (from bittorrent) the "ubuntu-5.10-install-i386.iso" and burned it with Nero, but half way through the installation it failed.  

I looked online and found info about md5sum's (which I had no idea about before) and checked my iso out.  Lo and behold, the numbers didn't match.  So I downloaded it again (3 times infact) off of different mirrors online and every single one does not match the md5sum number given on the server.

I have no idea if I'm doing something wrong (dunno how I could be) but seems weird that so many wouldn't match, and I don't want to just burn the cd's and try them out since I don't have many blank discs left and don't really want to waste them.

If anyone has any ideas please help :) Thanks in advance!!

---

### Post by Samuel on 2005-11-08
well i hope someone can advise you on whats going wrong as i dont know, 
but you could order the installation CD from LinuxISO.co.uk for &#163;1, or get the free one from shipit.ubuntu.com but i hear the free ones can take months to be delivered or may not even get delivered.

Have you tried downloading it from a different PC?

---

### Post by sevenrechlin on 2005-11-08
Well haven't tried that, but probably should.  Just don't want to use the other computers because they're crap :p.  Just tried my luck at downloading via bittorrent again but doesn't match, the one I got is:

d8fe75d2c3edc97679d729ab3a314263 *ubuntu-5.10-install-i386.iso

So dunno what to do, guess I'm gonna just try it anyways...

BTW: Some of the others I've downloaded are this:
15f330c19a7eff4159d04171054797ee *ubuntu-5.10-install-i386.iso
c44619a93adfe5c7d5c6c3bbe75ae1ad *ubuntu-5.10-install-i386.iso
be2bf9fdcc5734a41bf424573490ebbf *ubuntu-5.10-install-i386.iso

---

### Post by aysiu on 2005-11-08
[QUOTE=Samuel]or get the free one from shipit.ubuntu.com but i hear the free ones can take months to be delivered or may not even get delivered.[/QUOTE] Mine took two months--I think that's a fairly typical timeframe.

---

### Post by HJThis on 2005-11-08
Hey,To all

@sevenrechlin

May i ask please did you download it from here
& check the md5sum right from that site :confused: 

[http://us.releases.ubuntu.com/releases/5.10/](http://us.releases.ubuntu.com/releases/5.10/)

Best of luck

i would also like to add don't install it if the sum is not right
or if one of the Pros here say it's ok

---

### Post by sevenrechlin on 2005-11-08
Yeah that was the second place I tried downloading the iso from :???:

---

### Post by HJThis on 2005-11-08
Hi,sevenrechlin

Hmm that is odd i would hold off on downloading it
tell you get a heads-up from one of the Pros here
let them check it out for you.

Best of luck :confused:

---

### Post by sevenrechlin on 2005-11-09
Well first try downloading on another computer, complete success.  So it's official, my computer is doing something to corrupt the .iso files.  I have no idea what could possibly be doing this, but I have had problems with .iso files in the past (quite often infact).

If anyone has any clues to why my computer might be doing this (I'm wondering about WinRar?) please help me out :)

Thanks for the help and ideas!!!  It worked!! Now to install.

update: The .iso becomes "corrupt" as soon as it touches my computer (md5sum's don't match anymore).

---

### Post by SickTwist on 2005-11-09
Could there be a problem with the md5sum program on your computer?

---

### Post by sevenrechlin on 2005-11-09
Pretty sure, because it's the same file I copied over to the other computer to make sure it was OK.  If I can't figure it out I guess it doesn't matter too much now anyways...  Have Ubuntu installed, and am using it now :).  So guess I might just have to download ISO's here for now on.

---

### Post by Samuel on 2005-11-09
Good stuff, graveman is a good CD burner program and you can mount .ISO files directly from Linux :)

I'm wondering if anti virus software could cause this problem as it will unpack the ISO file to scan it, maybe corrupting the .ISO file? 

well anyway glad you finally got it up and running :)

---

### Post by ssam on 2005-11-09
burning iso in breezy is as easy as it gets.

download the file

right click on it

choose "write to disk"

easier than windows.

also i'd recommend using bittorrent to download isos. it has checksumming built in, and will redownload part of the file if it is corrupted. (and ofcourse it takes a load off the ubuntu servers by sharing it)

---

### Post by sevenrechlin on 2005-11-09
Yeah the antivirus thing is probably it...  Don't know what else would be causing it.  Worked fine on other two computers in the house, and neither had NAV or Norton Firewall.

---

### Post by Topsiho on 2005-11-10
I had the same trouble downloading big .iso files last year, trying different computers and different modems. It boiled down to a faulty ADSL-connection in the telephone exchange. Not that the telephone company ever admitted that but after my complaints this nasty problem suddenly diappeared....

Success in finding the cause of your problem, try your computer with the connection of someone else if that's an option.

Topsiho

---

### Post by HJThis on 2005-11-10
Hi,sevenrechlin

I would also install if you did not do so

chkrootkit & rkhunter

now that you have it installed, Ubuntu that is

& you will need them both anyway.

BOL ;)

---

