---
title: "Can I restart or Refresh Ubuntu 13.10 at a loss right now"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by keifus-rahn on 2013-12-02
Ive got a problem my Freind set up Ubuntu 13.10 along side Windows8.1 for me and he set up a random name and password well i just changed my acct name and password and changed it to admin Now i cant log in its telling me incorect password ive tryed and tryed t still nothing so is there any way to reset Ubuntu to like it was just installed? or any way to fix that problem?  I really dont want to lose 120Gb becuse of this :( any help will be apreciated.

---

### Post by Bucky Ball on 2013-12-02
Your friend doesn't remember the password and username? How did you change the account name and password? I'd suggest that was ignored and it is waiting for the password your friend chucked in.

---

### Post by keifus-rahn on 2013-12-02
> **Bucky Ball said:**
> Your friend doesn't remember the password and username? How did you change the account name and password? I'd suggest that was ignored and it is waiting for the password your friend chucked in.

I know what the password is ive been using that one he set up for a few days ive been trying both  but it still wont let me log in. I changed the password and adminastrator setting in settings under accts and i just check how much space he set up and its 220GB so i guess i need a new computer sence i just lost that much space on my laptop

---

### Post by Bucky Ball on 2013-12-02
Just install Ubuntu again. You don't need a new computer! Just wipe the drive and start again. Find your friend. ;)

---

### Post by jdeca57 on 2013-12-02
> **keifus-rahn said:**
> I know what the password is ive been using that one he set up for a few days ive been trying both  but it still wont let me log in. I changed the password and adminastrator setting in settings under accts and i just check how much space he set up and its 220GB so i guess i need a new computer sence i just lost that much space on my laptop
Could it be a problem with the keyboard layout? As a user of a Belgian keyboard I know how confusing that can be when you enter a password that is hidden...

---

### Post by keifus-rahn on 2013-12-03
I did what you said and reinstaled :)   But i have another issue now maybe you can help me out with???   " I don't think Ubuntu / linux likes me very much " :(

The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: gcc (>= 4:4.4.3) but it is not going to be installed
                   Depends: g++ (>= 4:4.4.3) but it is not going to be installed
 g++-multilib : Depends: cpp (>= 4:4.8.1-2ubuntu3) but it is not going to be installed
                Depends: gcc-multilib (>= 4:4.8.1-2ubuntu3) but it is not going to be installed
                Depends: g++ (>= 4:4.8.1-2ubuntu3) but it is not going to be installed
                Depends: g++-4.8-multilib (>= 4.8.1-4~) but it is not going to be installed
 libghc-bzlib-dev : Depends: libghc-base-dev-4.6.0.1-8aa5d
                    Depends: libghc-bytestring-dev-0.10.0.2-4f932
E: Unable to correct problems, you have held broken packages.

E. Malfourmed line 57 source list

---

### Post by Bucky Ball on 2013-12-04
Can you get to a desktop? If so, open a terminal and try these two commands one after the other, press enter in between, and copy paste any error messages you receive:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2013-12-04
* Posted as duplicate due to the lag monster. Disregard. *

---

### Post by keifus-rahn on 2013-12-04
> **Bucky Ball said:**
> Can you get to a desktop? If so, open a terminal and try these two commands one after the other, press enter in between, and copy paste any error messages you receive:

```
sudo apt-get update
sudo apt-get upgrade
```then when iy was compleat a box poped up saying


after i did sudo apt-get  This is what it returned= keith@keithrahn:~$ sudo apt-get update
[sudo] password for keith: 
E: Malformed line 57 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.

and when i did sudo apt-upgrade   It did alot of updating and this is the llast line of all the bla bla bla= update-initramfs: Generating /boot/initrd.img-3.11.0-14-generic

then a box poped up saying= Sorry ubuntu 13.10 has experienced an internal error.
E:Malformed line 57 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.

---

### Post by Bucky Ball on 2013-12-04
Could you open a terminal and:

```
nano /etc/apt/sources.list
```

... and post the output here, please.

---

### Post by keifus-rahn on 2013-12-04
> **Bucky Ball said:**
> Could you open a terminal and:

```
nano /etc/apt/sources.list
```

... and post the output here, please.


This is all that came up All blank.           And i also Want to say that i really do appreciate all your help :D
                                           

                                                                                                        TERMINAL                                                     
                                                 ------------------------------------------------------------------------------------------------------------------------------
                                               |           " GNU nano 2.2.6          File: /ect/apt/sources.list                 Modified " 
                                               |  |                                                                                                                             |
                                               | 
                                               | 
                                               |                                                    [ New File ] 
                                               |    ^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos 
                                               |    ^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell 
                                               ---------------------------------------------------------------------------------------------------------------------------------

now every five to ten min's im getting a pop up- E:Malformed line 57 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.
Should i change the topic of this thread?

---

### Post by Bucky Ball on 2013-12-05
This problem:

```
E: Malformed line 57 in source list /etc/apt/sources.list
```

Has a fix here at Answer 1 down the page:

[http://askubuntu.com/questions/285015/e-malformed-line-57-in-source-list-etc-apt-sources-list-dist-parse](http://askubuntu.com/questions/285015/e-malformed-line-57-in-source-list-etc-apt-sources-list-dist-parse)

As for your empty sources list, that is a complete mystery. Could you go to Software Sources (Update Manager and hit the Settings button in the bottom left corner). Does it have any repositories listed there? Are they unticked?

---

### Post by keifus-rahn on 2013-12-05
> **Bucky Ball said:**
> This problem:

```
E: Malformed line 57 in source list /etc/apt/sources.list
```

Has a fix here at Answer 1 down the page:

[http://askubuntu.com/questions/285015/e-malformed-line-57-in-source-list-etc-apt-sources-list-dist-parse](http://askubuntu.com/questions/285015/e-malformed-line-57-in-source-list-etc-apt-sources-list-dist-parse)

As for your empty sources list, that is a complete mystery. Could you go to Software Sources (Update Manager and hit the Settings button in the bottom left corner). Does it have any repositories listed there? Are they unticked?

Let me check But i wanted you to take a look at this for me this is whats on my drive i think somthing is wrong there to.

[COLOR=#222225][FONT=Arial]Partitions on drive C Using- "Mini Tool Partiton Wizard" [/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]      | capacity | | used |--- | unused |--- | File Sysyem |- | Type | | Status |[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]*:   SYSTEM / 300.00 MB 45.15 MB 254.85 MB FAT32 GPT (efi system)[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]*:   Recovery / 900.00 MB 338.78 MB 561.22 MB NTFS GPT (Reserve)[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]*:------------- /   128.00 MB 128.00 0 mb OTHER GPT (reserve)[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]C:------------ /[/FONT][/COLOR][COLOR=#222225][FONT=Arial] 191.44 GB 49.87 GB 141.57 GB NTFS GPT (data p...)[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]*:------------ /  85.00 GB 6.59GB 78.41 GB EXT4 GPT NONE[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]*: ------------ / 350.00 MB 285.43 MB 64.57 NTFS GPT (RECOVERY)[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]*:   Restore /  20.01 gb 9.19 GB 9.19 GB NTFS GPT (Recovery)[/FONT][/COLOR]

---

