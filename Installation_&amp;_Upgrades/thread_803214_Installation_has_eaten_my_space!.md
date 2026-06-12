---
title: "Installation has eaten my space!"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by paulcliman on 2008-05-22
********On a recent trip to UK, I bought a copy of "Computer Shopper", read about Ubuntu, returned to france and installed it - wonderful.
BUT ... I had a NTFS "**C**" drive, an NTFS "**D**" drive with lots of space(200Gb). I think I had a moment's inattention, because now my Linux partition is enormous and "**D**" only has 15Gb!
My question: can someone please explain to me (in fairly simple English) how can I shrink the Linux drive and get "**D**" to expand & fill the gap?
Thanks you in anticipation

---

### Post by NightwishFan on 2008-05-22
Did you install in Wubi or from the Live cd? You should not be "using" any more space than when you installed. You should pre-partition space. Use gparted (partition manager) on the Ubuntu Live cd to edit your disks.

---

### Post by paulcliman on 2008-05-22
I have NO idea what Wubi means, but I downloaded an ISO file from the Ubuntu site, burned a CD and installed from there; there was at one point a question about space but I was becoming a little lost and seemed just to accept the default offerings!
Does this help you?

---

### Post by NightwishFan on 2008-05-22
Wubi is an "inside windows" installer where you run with Windows booted. If you rebooted, and did the start Ubuntu, and then installed from inside the Ubuntu session, then its full. Let me see the layout of your disk. In Ubuntu:
Press alt+f2 then type:
```
xterm
```
Push enter, and a little box will come up. In the box copy and paste:
```
sudo fdisk -l
```
Push enter and type your password (it wont show up) then push enter again.
Paste the results here.

---

### Post by iaculallad on 2008-05-22
Did you do package installations, disto update? If so, you could issue the command **sudo apt-get clean** in your terminal to clean up your cache.

---

### Post by tommcd on 2008-05-22
1) Can you still boot Windows? When you boot up your PC, does the grub menu give you a choice of booting Ubuntu or Windows?
2) Open a terminal (applications > accessories > terminal) and post the output of "sudo fdisk -l" (without the quotes).

---

### Post by paulcliman on 2008-05-22
> **NightwishFan said:**
> Wubi is an "inside windows" installer where you run with Windows booted. If you rebooted, and did the start Ubuntu, and then installed from inside the Ubuntu session, then its full. Let me see the layout of your disk. In Ubuntu:
Press alt+f2 then type:
```
xterm
```
Push enter, and a little box will come up. In the box copy and paste:
```
sudo fdisk -l
```
Push enter and type your password (it wont show up) then push enter again.
Paste the results here.


Oh dear!
Following your instructions, I get to xtermPush (enter)
and receive a box saying "Could not open location file:///home/paul/xtermPush!

---

### Post by NightwishFan on 2008-05-22
xtermpush? If you followed them wrong nothing would happen.

---

### Post by paulcliman on 2008-05-22
Ah ......... my mistake, sorry! I misread your instructions.
RIGHT, followed instructions and received the data you asked for.
HOWEVER, this may seem a really stupid question to you, but in this Terminal box, I can find no menu with the possibility of "copy" and CTRL/C doesn't work. I opened OpenOffice and tried copying & pasting a few times without success. Does linux hav a different shrtcut for this?

---

### Post by paulcliman on 2008-05-22
Another fgrustrating problem for me is, I have to keep rebooting between Vista & Ubuntu because I cannot yet access the internet via Ubuntu 5this was going to be a later posting for you very kind people helping on this Forum! Therefore, I t takes me time to respond, as you see.
It is SO frustrating - this Ubuntu looks so good but there are so many problems!

---

### Post by Sef on 2008-05-22
> Another fgrustrating problem for me is, I have to keep rebooting between Vista & Ubuntu because I cannot yet access the internet via Ubuntu

How are you connected to the internet?

A) Dial up

B) Broadband

C) Other

---

### Post by paulcliman on 2008-05-22
By Broadband. I'm in france and connect to wanadoo.fr via a sagem modem

---

