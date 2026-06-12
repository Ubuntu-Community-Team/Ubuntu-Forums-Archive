---
title: "Updates impossible to install"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by KarmicKlot on 2010-08-08
I have installed Lucid Lynx, which has proved a complete disaster after the useable and trouble free Karmic Koala. First problem is that every attempt to connect to the internet requires me to put in my router authentication key, which Karmic Koala remembered, and Lucid Lynx does not. Second problem is that every couple of minutes it drops the connection to my router and requires the key to be input again, swiftly followed by my admin password. 
 
Even if I can keep the connection to the router going long enough to try, any attempt to run Update Manager fails with every update giving a message like:
"W. Failed to fetch http.//security.........
.....could not resolve 'security ubuntu.com' "
 
Does anyone have a solution to these problems, or should I just delete the Ubuntu partitions with G parted and clean install Karmic Koala?

---

### Post by mörgæs on 2010-08-10
Did you have wired internet access while installing 10.04? This will prevent a lot of trouble.

9.10 is supported through april 2011, so it is a good option, if everything else fails. At that time you can try 10.04 and/or 10.10.

---

### Post by lechien73 on 2010-08-10
What wireless network card do you have? To find out, open a terminal window and type:

```
lspci

```
Then post the card details here. There may have been a fix posted for this already.

---

### Post by Q2299 on 2010-08-10
I have just installed 8.04 in my ACERLaptop.
Good things first: The wireless works fine.
Able to Browse with mozilla etc....
Now the trouble: BIG TROUBLE::
 Cannot UPGRADE or UPDATE. Always asks for the cd to be inserted. But does not connect to it. The response is no autorun found! The cd shows up on the screen.
The laptop version is very limited.
I am going to ORDER a 10.04 LTS CD from official UBUNTU and try. It takes 8 weeks to receive it...maybe.
The download is a 10.04 but it only loads the 8.04!!!!
Can any one help???
Q2299

---

### Post by mörgæs on 2010-08-10
Q2299, you are double-posting AND hijacking a thread. This will not bring you closer to an answer.

---

### Post by KarmicKlot on 2010-08-10
I did not have wired connection when I installed 10.04
With a wired connection I was able to download updates from Update Manager, but wireless connection will not work. All I get when I input lspci into a terminal is "command not found" and "did you mean Command 'lspci from package 'pciutils'." 
I am unsure whether the first letter is a large or small L or i or the number 1, and have tried all combinations without success.
 
I have looked in Synaptic package manager, and found that the latest version of the package pciutils is installed.
 
Incidentally 10.04 drives me crazy by constantly demanding my admin password, default keyring password and wireless encryption key, despite the fact that the encryption key is now memorised, and both Secret Storage Service and SSH key agent are not run at startup.

---

### Post by KarmicKlot on 2010-08-10
Another thought.  I have tried to get Ubuntu to identify the inbuilt wifi adapter in the laptop without success, but the machine is dual boot with Windows Vista, and the latter simply identifies it as a Ralink 802.11n wireless adapter, but does not identify a specific chipset.  digging deeper in Windows actually gives the maker as Foxxcon!  I have searched the forum for posts about Ralink wireless adapters but have not found anything that gave a solution.

---

### Post by jcolyn on 2010-08-10
The wireless driver is not installed during the install process. You have to go to system-administration-hardware drivers. It will take a couple of minutes but if your card is supported it will then let you download and install.

---

### Post by KarmicKlot on 2010-08-11
Thank you,  I tried that.  First it shows "Searching for available drivers",
then produces an empty window headed "No proprietary drivers are in use on this system."

---

### Post by KarmicKlot on 2010-08-11
This morning I actually achieved a wireless connection useing Wicd for long enough to download my home page, and then load another page, but after a minute it dropped the connection. I reconnected, but second time round the connection was again dropped in a few seconds.
 
edited because the word man**** (think manager) is not allowed by the swear filter or whatever!

---

