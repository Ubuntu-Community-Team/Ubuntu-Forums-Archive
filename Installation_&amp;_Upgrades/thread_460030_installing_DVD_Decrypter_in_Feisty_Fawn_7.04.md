---
title: "installing DVD Decrypter in Feisty Fawn 7.04"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by xjgnsdof on 2007-05-31
Hi. I am having trouble finding online instructions for installing DVD Decrypter (which apparently I have to do by installing something called "Wine") that aren't outdated or vague.

How do I install DVD Decrypter via Wine?

---

### Post by renzokuken on 2007-05-31
install wine (its in synaptic)

get the DVDDecrypter exe file and save it to your home folder. for the sake of this post i'll call it dvdd.exe

run

```
wine dvd.exe
```

this will install it to

/home/username/.wine/drive_c/Program\ Files/DVD\ Decrypter or something like that for the last directory

to run it do

```
cd /home/username/.wine/drive_c/Program\ Files/DVD\ Decrypter/
wine *.exe
```

---

### Post by xjgnsdof on 2007-05-31
I installed and ran DVD Decrypter, but I get the following message in Terminal:

Fontconfig error: "~/.fonts.conf", line 2: no element found

Then, it says that no devices are found.

---

### Post by renzokuken on 2007-05-31
install the mscore fonts, they are in synaptic, or maybe automatix, cant remember.

the backslashes above are used to indicate a "space" when typing into the terminal

---

### Post by xjgnsdof on 2007-05-31
I already have those fonts; I re-installed them in Synaptic, but got the same error message (it actually printed twice this time and last)

I have two fons.conf files, which is probably why I got the error message twice:
1) in /etc/fonts, line 2 of font.conf says "<!DOCTYPE fontconfig SYSTEM "fonts.dtd">"
2) in /var/lib/defoma/fontconfig.d", line 2 of font.conf says "<!DOCTYPE fontconfig SYSTEM "/etc/fonts/fonts.dtd">"

More importantly, it still says in the "Source" drop down menu "No Devices Detected!" As long as DVD Decrypter runs, then the fonts error doesn't really bother me. How do I get it to recognize my DVD burner, though?

---

### Post by xjgnsdof on 2007-06-01
up

---

### Post by xjgnsdof on 2007-06-03
Never mind...I created a link between my DVD-RW drive and the Wine-emulated one in Terminal. It's working just fine, now.

---

### Post by kjberg2000 on 2007-06-03
I'm having the same problem...could you tell me exactly how you "created a link between my DVD-RW drive and the Wine-emulated one in Terminal"

---

### Post by kjberg2000 on 2007-06-03
More info: Feisty, AMD64, WINE 9.37

output from "ls" below, with -- then without a DVD in the drives; 

DVD Decrypter installed with DVDs in both drives

winecfg Windows Version is set to NT 4.0 

[email]xxxx@ubuntu:~/.wine[/email]/dosdevices$ ls f:
32bit        cdrun.exe   iclient      media       setup.inx
acrobat      comfed.1ph  id           perudi      tax.scd
answrks      data1.cab   ie           qkn2006     tax.thp
autoptch     data1.hdr   import       quicken     ttax.ico
autorun.exe  data2.cab   issetup.dll  scd         turbotax basic 2006 retail
autorun.inf  dlinst      layout.bin   _setup.dll  uninstal
autorun.ini  fonts       license.txt  setup.exe   volumeicon.icns
background   forms       macscan.txt  setup.ini   winscan.dat

[email]xxxx@ubuntu:~/.wine[/email]/dosdevices$ ls e:
cdrom1

[email]xxxx@ubuntu:~/.wine[/email]/dosdevices$ ls f:
cdrom0

Any idea why I still get "No Devices"?

---

### Post by knutkracker on 2007-06-05
This should work:

[http://nikdoof.net/perma/using-dvd-decrypter-on-ubuntu-wine](http://nikdoof.net/perma/using-dvd-decrypter-on-ubuntu-wine)

---

### Post by rbmorse on 2007-06-05
Whats wrong with k9copy?  Does DVD-d do something k9copy won't?

---

### Post by xjgnsdof on 2007-06-07
In Terminal, input &#8220;cd ~/.wine/dosdevices&#8221; then &#8220;rm h:&#8221; (where h: is the DVD-RW drive in Wine) then &#8220;ln -s /media/cdrom -s h:&#8221; then &#8220;ln -s /dev/hdd -s h::&#8221;

In response to the last post, DVD-Decrypter allows you to rip DVDs that are copyright protected for back-up purposes.

Has anyone else figured out the fonts.config error?

---

