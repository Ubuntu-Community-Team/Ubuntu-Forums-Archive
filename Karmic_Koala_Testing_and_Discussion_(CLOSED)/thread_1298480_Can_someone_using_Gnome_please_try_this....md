---
title: "Can someone using Gnome please try this..."
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-10-22
With nautilus, expand filesystem/usr and click on bin. Note how many seconds it takes before the files are listed. Time only the first attempt, as subsequent times will be shorter due to caching I guess.

My results with an eeeBox 202 (1.6 GHz, 1 Gb memory) just booted:

Jaunty ext3: 2762 files takes 18 seconds

Karmic ext3: 1573 files takes 2 mins 23 seconds

Seeems a bit long to me.
Cheers Mike

Edit:
It seems it has to do with 'icon' or 'list' view. I always use list view and that causes it to take over 2 mins. If I use icon view it takes around 20 seconds.
Select (say) /usr/bin and with the dropdown control change to List view from Icon view. It takes ages to show the result on my machine. Switch back to Icon or Compact view and it's much quicker to display.

---

### Post by flipper9 on 2009-10-22
Karmic 9.10 with all patches applied as of 10 minutes ago: 1755 files in /usr/bin
21 seconds
Asus EEE 1000h 1.6Ghz Atom processor, 2gb RAM, stock 160gb SATA hard drive

Course, I could have opened that folder days ago (though not today) and it's cached or something.  Dunno.

---

### Post by linusr on 2009-10-22
Karmic: 1429 files, instant didn't notice any lag

I'm using ext4 file system on Dell Vostro 1500

---

### Post by linusr on 2009-10-22
Karmic: 1429 files, instant didn't notice any lag

I'm using ext4 file system on Dell Vostro 1500

---

### Post by cariboo on 2009-10-22
1486 files, about 9 seconds.

---

### Post by Rob2687 on 2009-10-22
1359 items, ~7 seconds

Pentium M 1.7 Ghz, 1GB DDR, 30GB IDE drive.

---

### Post by sports fan Matt on 2009-10-22
10 seconds here

---

### Post by Longinus00 on 2009-10-22
core duo t2300 (1.0 ghz when browsing nautilus)
slow laptop 60gb hard drive (5400rpm)

1494 items and around 9 seconds

Anybody know what the executable "[" does?

---

### Post by KrazyPenguin on 2009-10-22
Fresh install, took 8 seconds , 1568 files.

this is with exaile streaming the BUZZ FM181, firefox running, oo, and package installer running on a dual core centrino toshiba laptop.

Haven't tweak her yet.

;-)

---

### Post by amauk on 2009-10-22
1920 files
10 secs

> **Longinus00 said:**
> Anybody know what the executable "[" does?it's a program that takes arguments for comparison, and is used by Bash.
It's named "[" so that the format of conditional statements mimics that of C, et al.
```
if [ $some_value -eq 0 ]; then
```
sends the arguments
```
$some_value -eq 0 ]
```
to [
[ then returns true or false depending

---

### Post by drs305 on 2009-10-22
7 seconds, ext4, 1630 items.

---

### Post by Longinus00 on 2009-10-22
> **amauk said:**
> 1920 files
10 secs

it's a program that takes arguments for comparison, and is used by Bash.
It's named "[" so that the format of conditional statements mimics that of C, et al.
```
if [ $some_value -eq 0 ]; then
```
sends the arguments
```
$some_value -eq 0 ]
```
to [
[ then returns true or false depending

Thanks for clearing that up!

---

### Post by Barriehie on 2009-10-22
Nautilus 2,052 files / 13 seconds
Thunar   2,052 files / 2 seconds

Barrie

---

### Post by cjazz on 2009-10-23
7 seconds, ext4, 1471 items

---

### Post by ankspo71 on 2009-10-23
Hi,
I just finished a clean install of Karmic RC, and /usr/bin took about 4-5 seconds to open in icon view. 1,388 items, totalling 125.2 MB  Using Ext4 filesystem on the PC in my sig. Firefox (one tab) open and tranmission (nice=5) is transferring slowly in the background. Nvidia 185 driver is enabled so compiz is running too.
James.

---

### Post by SunnyRabbiera on 2009-10-23
4 seconds, and thats with EXT3

---

### Post by mdurham on 2009-10-23
Thanks for all the replies.
So, any ideas on why my system takes over 2 minutes? What can I try? I have Karmic on another partition and it's just the same.

Cheers, Original poster

---

### Post by namluc on 2009-10-23
I counted to 21 elephant, 1792 files, ext 4, intel atom netbook

---

### Post by philinux on 2009-10-23
About ~6 seconds here. 1592 items.

---

### Post by howefield on 2009-10-23
I guess hardware will have a huge impact on the results, ideally you want to compare with someone elses eeeBox.

FWIW (ie, nothing because of the hardware)

1525 Files = 4 seconds.

---

### Post by 00b00nt00 on 2009-10-23
Instant, 1,320 items.

Eee PC 900HA

---

### Post by philinux on 2009-10-23
> **philinux said:**
> About ~6 seconds here. 1592 items.

Just installed thunar. Result **instant** display.

Guess nautilus needs some love. :P

---

### Post by flipper9 on 2009-10-23
The closest thing to your eeebox would be something with an Atom processor.  The two I noticed listed in the results were both 21seconds to load that directory.

---

### Post by AlphaLexman on 2009-10-23
nautilus = 21 sec
thunar  = 2 secs
dolphin = 2 secs, but conky says processor use is high for 4 1/2 mins!

ext3, amd dual core 6000

---

### Post by kimberlite on 2009-10-23
Actually, my Nautilus is unable to open that folder (/usr/bin/). I have to kill the process since it consumes all of the cpu on toshiba a300 dual core notebook. Very annoying.

---

### Post by mdurham on 2009-10-23
> **kimberlite said:**
> Actually, my Nautilus is unable to open that folder (/usr/bin/). I have to kill the process since it consumes all of the cpu on toshiba a300 dual core notebook. Very annoying.

Yes, I can get this too sometimes. And when I kill Nautilus, all the icons are removed from the desktop. They remain removed until I log-in again.
Anyway, see my first post for a bit more info.

---

### Post by ranch hand on 2009-10-23
Mine is instant.

What on earth are you doing with 9.10 installed on ext3?

---

### Post by kimberlite on 2009-10-23
I have found an unresolved bug report, that is probably related to this issue here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/298663](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/298663)

---

### Post by kimberlite on 2009-10-23
> **ranch hand said:**
> Mine is instant.

What on earth are you doing with 9.10 installed on ext3?

I am on ext3 and using Jaunty.

---

### Post by gjoellee on 2009-10-23
1,413 items

Nautilus: 6 sec
PCManFM: Less then 1 sec

AMD Athelon 3000+ (2.16 GHz), 2 BG DDR2 RAM on ext4

---

### Post by drs305 on 2009-10-23
I repeated it with PCManfm as well, which I normally run as root.
Nautilus as user: 7 seconds
PCManfm as root or user: 1 second

---

### Post by ranch hand on 2009-10-23
I like pcmanfm too.  I like Lxde too.  I am hoping they get Lubuntu up and running.

---

### Post by lazka on 2009-10-23
The second will always be faster because of caching.
To remove the cache: ```
sudo sync; sudo echo 3 | sudo tee /proc/sys/vm/drop_caches;
```

---

### Post by Seventh Reign on 2009-10-23
didnt have a stopwatch handy but 1938 files opened in around 10 seconds .. give or take 2

Ext 4

---

### Post by philinux on 2009-10-23
> **lazka said:**
> The second will always be faster because of caching.
To remove the cache: ```
sudo sync; sudo echo 3 | sudo tee /proc/sys/vm/drop_caches;
```

Ah that explains why thunar was faster. Now both are the same, ~6 secs.

---

### Post by AlphaLexman on 2009-10-23
Yes, my thunar results were in the 21 sec range after clearing the cache. Although Dolphin still showed the first few rows of icons it STILL took almost five minutes of processing power to read the full directory.

---

### Post by ArtLaForge on 2009-10-23
1391 files
5 seconds

Desktop #1 in sig.

---

### Post by nanog on 2009-10-23
Upgraded karmic 2436 files 8 seconds.

---

### Post by mdurham on 2009-10-23
Nobody says if they're using icon or list view. Try switching between the two using the drop-down control and note any diff in time.
Cheers, Mike

---

### Post by mdurham on 2009-10-24
I found the problem by a process of elimination. Something was wrong with ~/.gconf/desktop/gnome/interface/%gconf.xml
If I remove that file nautilus works as it should, replace it and it goes slow again. So if nautilus is slow for you, try deleting that file.
Cheers, Mike

---

