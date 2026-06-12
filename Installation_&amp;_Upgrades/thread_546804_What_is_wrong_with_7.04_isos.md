---
title: "What is wrong with 7.04 isos?"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Lockheed on 2007-09-09
Here is what happens when I try to bootup the newest ubuntu cd:

[IMG]http://www1.zetosa.com.pl/conrad/ubuntu.jpg[/IMG]

I tried it with isos for both 64 and 32 architecture. I downloaded it coupe of times and I run it on two different laptops:
First, Acer 4404 with Radeon X700 after first try did not start anymore (burned GPU).
Second, Compaq v6000 behaves the same  but luckily does no get damaged.
Every time such picture appears when Gnome should start
It starts with black and then gets brighter and brighter, then again it gets dark from the edges to the centre. Looks very much like picture given by burning GPU.

What is wrong with this release?

---

### Post by mikewhatever on 2007-09-09
Have you tried other releases and they worked? Have you [MD5SUM -ed]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29")?

---

### Post by Pumalite on 2007-09-09
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Lockheed on 2007-09-09
Md5Sum shows correct value. 
Older verions of ubuntu work as well as other distributions.
I know how to record images (Nero) and verification was always successful. 
I used three different cds.

Any other ideas?

---

### Post by merlinus on 2007-09-09
It would seem related to your video card.

Do you get to the opening menu?

---

### Post by almostalive on 2007-09-10
> **Lockheed said:**
> Md5Sum shows correct value. 
Older verions of ubuntu work as well as other distributions.
I know how to record images (Nero) and verification was always successful. 
I used three different cds.
Any other ideas?

I have a related problem.. I'm not able to install ubuntu 7.04
I also have a Radeon graphic card..

I don't think ubuntu 7.04 is compatible with our cards.. :-/
I'm going to burn 6.06 now. hopefully this version works.

---

### Post by Pumalite on 2007-09-10
If you have a problem with your graphics, go for Alternate CD, text based mode to avoid those problems.

---

### Post by Lockheed on 2007-09-12
I did but this problem will reoccur after installation during first boot when gnome starts.
It is NOT the problem of my graphic card because I had the same problems on laptop with Radeon X700 and now on Geforce 6150.

How is it possible that authors of this version issued it with such bug?

---

### Post by Lelouch on 2007-09-12
i suppose u downloaded it from a direct link... didn't u?

the same happened to me.. but when i downloaded a copy using torrent client, it worked correctly...

---

### Post by Pumalite on 2007-09-12
Torrents always better than HTTP or FTP

---

### Post by Lockheed on 2007-09-12
Torrent is slow. Besides what's the differences if the file sum is legit?

---

### Post by soapytheclown on 2007-09-13
the pic uve got there looks like how my compaq v6000 did when i didnt use the boot flags, i wrote a tutorial on how to install fesity onto the v6000 if u want to check it out  [http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000](http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000)

btw i burned using and installed on the dvd writer on the v6000 but i did notice someone else mentioning the isos he burnt using a v6000 were coming out corrupt :S

---

### Post by Lockheed on 2007-09-23
Thank you soapytheclown. Your flags solved the problem.

---

