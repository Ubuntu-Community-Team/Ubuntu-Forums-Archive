---
title: "How to install ubuntu studio ?"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by 3delic on 2007-05-11
Hi all, since the install image is 860 megs I cant burn it to cd ...
Or is it easier to direct install the packages on feisty ?

Thanks

---

### Post by Psicolonia on 2007-05-11
yes you can, there are 80 min, 90 min and even 100 min cds, you have to overburn them. i think it would be easier to install from the image.

---

### Post by 3delic on 2007-05-11
And how do I install ubuntu studio from the downloaded image on a HD ?
Is it a bootable LiveCD ?

---

### Post by n00blar on 2007-05-11
If you burn them to a 80min CD you'll have to problems.

---

### Post by 3delic on 2007-05-11
Yes, but how to install from the image ?
Can I do it from the feisty dawn deskop cd, looking for the image on the HD from there ?
And install it in another partition ?

---

### Post by GadgetsGuy on 2007-05-13
I would also be very interested in this, as I do not have a DVD burner either - only a CD-RW burner

I have TONS of 80min CDRs that I buy bulk, so I am not really interested in having to buy 90 or 100min overburn CDRs (which I have had nothing but problems with in past experiences anyways)

bookmarking this thread - thank you

---

### Post by heartbeat on 2007-05-14
I also tried to burn it on a 80 min cd and it didn't work. nero told me that the cd was nog big enough

---

### Post by Endolith on 2007-05-14
I don't have a DVD burner, so followed the directions on the download page.  To reiterate:

[LIST=1]
[*]I used a regular Feisty CD to install Feisty
[*]Open a terminal and enter these two lines:```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```
[*]Open Synaptic and search for "ubuntustudio", then install any packages you want, such as the desktop, audio package, etc.
[/LIST]

It seems to work fine.  Just requires downloading the packages.

---

