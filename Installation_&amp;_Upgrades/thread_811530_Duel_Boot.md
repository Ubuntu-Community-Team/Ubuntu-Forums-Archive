---
title: "Duel Boot"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by gregrae on 2008-05-29
I have installed Windows XP pro , Vista Enterprise , and I am trying to install Ubuntu. 
At the partition Section I have the 3 partitions .
one with XP the other with Vista and the next Partition for Ubuntu being 27,595 MB but after the size of this partition is ( unknown ). and when I go next the promt on the monoter is 
No root file system is defined.
Correct this from the partition menue.
Where do I find this section and what do I have to do for the installation to continue.
Thank you Greg.
I am going to use GAG V4 ( Graphical Boot Manager to be able to boot of any one of the 3 OS .

---

### Post by mamyte18 on 2008-05-29
Premium Membership

Upgrade your account and earn more with Bux.to. The Premium Membership comes with the following features: 
» Surf Ads guaranteed loaded with minimum 20 ads every Day!
» Earn $0.0125 each click and $0.0125 each click from your referrals.
» Priority Payments.
Exclusively for premium members: Get your Prepaid Bux.to MasterCard®
Earnings Example
» You click 20 ads per day = $0.25
» 25 premium referrals click 20 ads per day = $6.25
» Your monthly earnings = $195.00
» Your total annual earnings = $2,340.00
Processing time: 2 working days.
I'm so proud of everybody, who clicks for bux.to and everybody who works at bux.to, they made a fantastic system. You are clicking for a wanderful system. I joined bux.to in the middle of January, but I have to admit that I wasn't brave enough to invest 500$-s with no previous knowledge about the system. So I only bought 115 refs and a premium to test bux.to and I saw that the money is comming back really fast, so in March I bought another 335 refs. So totally I invested 500$-s.

Now I reached 1000$, I duplicated my investments in 1 month. Thank you bux.to! Thanks for the clickers and the advertisers, who made bux.to a smooth running machine! Thanks for everybody, who writes success stories to make people trust the system! And finally, thanks for my referrals, especially for the guy, who bought premium membership 1 week after joining!

We have to continue our journey through the ads. Good luck for everybody!
  
Steps how to register to bux!

1 step:  [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18)   go to this site. And register here.
2 step:  [http://www.alertpay.com](http://www.alertpay.com)
Then "SIGN UP", choose your country, then "Personal Starter" and "Get Started"; and write your name and other information. Where need.
Then you will receive a message to your email address.

When the alertpay are created go to link [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18), then"I Accept the Terms of Service” and  click butoon register.   And that’s all. You are the member.

To look videos click "Surf Ads". And you will earn your money.
Good luck. Odeta.
If there are ome problems write to me I could help you I promise. [email]odetux18@yahoo.com[/email]

---

### Post by housam on 2008-05-29
Boot from ubuntu live cd and type in the terminal ( applications >> accessories >> terminal )
```
sudo fdisk -l
```
where -l is a small L and post the results.

also after installing ubuntu you'll have a trible boot , you can read about it [[COLOR="Red"]_here _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by gregrae on 2008-05-29
Where do I find   ( sudo fdisk -1 )so I can download the f Disc to a floppy.
Can you give me a screan dump of the page where I type 
( applications>>accessories>>terminal}I am not familiar with ubuntu as I am trying to understand the OS . That is why I am duel butting so I can use the OS as I would like to use Linux I only have 1 PC and HD
Thank you for your patience and Help.

---

### Post by housam on 2008-05-30
put the ubuntu cd in the cdrom and start the computer. this will operate the ubuntu system from the cd. in the upper panel click on the word applications then accessories then terminal . then a window will pop-up to you . this window named the terminal which we can write codes inside it to get information ao apply changes or operate programs or install them.
after that you will type this code 
```
sudo fdisk -l
```
in the terminal and press enter. you will get the informations we want to know to help you .post this information .

---

### Post by zvacet on 2008-05-30
It should look something like [this.]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron")

---

### Post by gregrae on 2008-05-30
I hope this is the Information you require.
What do I do from this point.

---

### Post by housam on 2008-05-30
Repeat it as -l is a small L not 1.
```
sudo fdisk -l
```

---

### Post by lukydude on 2008-05-30
if it helps you with your isue mine when i do it looks like:

luke@luke-desktop-ubuntu:~$ sudo fdisk -l
[sudo] password for luke: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x418e418d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3628    29141878+   7  HPFS/NTFS
/dev/sda2            3629        4734     8883945   83  Linux
/dev/sda3            4735        4865     1052257+  82  Linux swap / Solaris
luke@luke-desktop-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x418e418d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3628    29141878+   7  HPFS/NTFS
/dev/sda2            3629        4734     8883945   83  Linux
/dev/sda3            4735        4865     1052257+  82  Linux swap / Solaris

---

### Post by zvacet on 2008-05-31
@ **gregrae**


> but after the size of this partition is ( unknown ). and when I go next the promt on the monoter is 
No root file system is defined.
Correct this from the partition menue.

Please look at link I posted to you.Step 4 of 7 is what are you looking for.

---

### Post by gregrae on 2008-06-01
This is a new screan dump.
What do I do with this information do I follow the steps 4 to 7.
do I have to coppy the information into the unbuntu installation.
In the Prepare disk Space of the insterlation do I go to manual.
I am a bit lost what I have to do with the f disk information.
greg

---

### Post by gregrae on 2008-06-04
Zvacet could you advise me is the screen dump give you the correct Information.
Sorry about persisting with this issue but I am trying to learn about Ubuntu.
Thank you Greg

---

### Post by zvacet on 2008-06-04
Just follow installation guide from link I posted to you.Sorry,but I didn´t read all guide so we will correct that now.In the guide you will find **Select how you want to partition the disk and proceed.**  Select manual and then new window will pop up.In that window select where you want to install Ubuntu and after that you should see step 4 of 7.If anything is still unclear please post back.I or somebody else will help you to install Ubuntu and enjoy it after that.Good luck!

---

### Post by gregrae on 2008-06-30
I have Installed Xp Pro. Vista Premium, and Ubuntu and Can boot from either one on startup selection but I would like to use GAG Which I have Installed and have running can Select the appropriate icon XP or Vista or ubuntu but when select ubuntu it comes up sector boot not found or Invalid.
What do I do to fix this problem as I want to use Gag.
Thank you Greg.

---

