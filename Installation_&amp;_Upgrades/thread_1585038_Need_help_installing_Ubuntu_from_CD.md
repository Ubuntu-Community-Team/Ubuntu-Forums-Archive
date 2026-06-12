---
title: "Need help installing Ubuntu from CD"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by ilikejellolol on 2010-09-29
Alright, so I followed the step by step instructions from this page:
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
When I downloaded the file, the file appeared on my desktop as an unknown file with the name "ubuntu-10.04.1-desktop-i386". I thought this was strange because it didn't have the ".iso" after it. I tried looking for a download location for the file that would give me a .iso file, but whenever I download the file it just appears on my desktop as "ubuntu-10.04.1-desktop-i386". After that, I downloaded Infra Recorder, and followed those instructions. Everything was going fine and when the progress bar hit 100%, Infra Recorder gave me some kind of error. I can't recall exactly what it said, but it said to check the log file or something like that. 
 
I wasn't sure what to do at this point, so I tried installing Ubuntu anyway. I rebooted with the CD and it took me to the burgundy screen and it started to load, but then the installation crashed to an MS DOS screen with some gibberish that I didn't understand.
 
Obviously the CD I wrote didn't have all of the installation files it needed. What should I do? Is there something wrong with the file that I downloaded? 
 
My computer is a Dell Vostro 200 and I am running Windows XP

---

### Post by Goolie on 2010-09-30
Try downloading one of the alternative installation CD's.  Try, adding the .iso manually, such as renaming it to foo.iso

I'm not familiar with Infra Recorder, I'm assuming it handles ISO burning since you got the burgundy screen.  

Try replicating and posting the Infra Recorder error and the final text that you get when Ubuntu's CD fails to boot.  This can help us a bit.

=D

---

### Post by lisati on 2010-09-30
<sidenote>Windows has a habit of hiding the file extension</sidenote>

---

### Post by Goolie on 2010-09-30
Yea, I haven't used Windows in a *while*.

=X

---

### Post by 23dornot23d on 2010-09-30
If you can post a photo of the gibberish ...... it may help .... work out what went wrong

other than that do it again ..... this time use k3b ...... from linux ......

apt-get install k3b

and its best to check the number ..... that it gives to say that its ok ..... 
burning at a lower speed too always seems to help ...... x 4  .......

---

### Post by Goolie on 2010-09-30
> **23dornot23d said:**
> If you can post a photo of the gibberish ...... it may help ....

other than that do it again ..... this time use k3b

apt-get install k3b

and check the number ..... that it gives to say that its ok ..... burn at a lower speed too
always seems to help ......

Wait, apt-get works in WinXP!?

The lower speed can help, actually, I *ALWAYS *use the slowest burn method possible.  But I'm a very patient person, so maybe you can do one above the slowest burn speed. Lol.

---

### Post by 23dornot23d on 2010-09-30
I am used to doing everything in Linux now ..... it does mention the program that the OP
is using in the write up ..... 

seems to go straight to 10.10 too from [Distro Watch and the link to Ubuntu Download]("http://distrowatch.com/table.php?distribution=ubuntu")

 ... and that's still the development version ...... for another 11 days at least .....

The [download page the OP shows]("http://www.ubuntu.com/desktop/get-ubuntu/download") 

That download page has everything on it but the two bits of info you need to see

The **Ubuntu version you are burning and the checksum** to make sure its ok .......

Progress ..... :confused:

Thats the correct file though ..... 

[COLOR=Blue]**ubuntu-10.04.1-desktop-i386**[/COLOR]

Just need a checksum ..... where is that now ?

[COLOR=Blue]**9a95ed6f6ec38fb58c446dba1add6a08 9a95ed6f6ec38fb58c446dba1add6a08 **[/COLOR]

Make sure that this number is ok [SEE LINK]("https://help.ubuntu.com/community/HowToMD5SUM")

matches the one shown in the burner ..... saves wasting a disk ..........

[Link to all the checksums]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by ilikejellolol on 2010-09-30
Got it to work! Thanks guys.

---

### Post by 23dornot23d on 2010-09-30
Nice one ...... mark as solved using the **[COLOR=Red]thread tools [/COLOR]**above the first post please ):P

---

