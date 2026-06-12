---
title: "Update interrupted, now errors"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by indyrenegade on 2011-10-14
Hello, I am relatively new to Ubuntu..

    This has been my first time updating, and I messed it up.. I needed internet connection to update, but my connection dropped, and typically when that happens (regardless of if I turn the WiFi switch on and off, that won't help pick the signal back up in quite a few cases) I have to force close my computer and turn it back on to get it back. So, that's what I did. After I turned it back on, it opened the usual boot screen, then proceeded to list off this: 


[B]
             Ubuntu 11.04
              .    .     .     .

             Ubuntu 11.04
             .    .     .     . * Checking battery state... [ OK ]

[/B]                
                                [B]*Setting sensors limits       [ OK ]

peech-dispatcher disabled; edit etc/default/speech-dispatcher 

                                *Starting bluetooth            [ OK ]

*PulseAudio configured for per-user sessions
                                                               sane enabled; edit etc/default/saned

                          *Enabling additional executable binary formats binfmt-support [ OK]

[/B]      
I know it wasn't a particularly conscientious decision on my part to force close during an update.. but now my computer hasn't left that screen with the text listed above in a while, now.. Any ideas? Is there any way of safely getting out of it and completing the update, or at least saving what I had? I'll wipe it and re-install if necessary. Thanks in advance!

---

### Post by 23dornot23d on 2011-10-14
try pressing 

Ctrl+Alt+F1

can you get to a login prompt ?

---

### Post by indyrenegade on 2011-10-14
Yes, it's reading.. 

[B]Boot from (hd0,0) ext3 8d200a6b-1c22-41fe-8ec5-1830020869af
Starting up...

Ubuntu 11.04 eileen-laptop tty1

eileen-laptop login:[/B]

I am assuming I should enter my comp password here, not my username. Just making sure. :)

---

### Post by 23dornot23d on 2011-10-14
enter your username first

then it will ask for your password


once you are in .....

do 

sudo apt-get update

( will see if you have a internet connection - if it updates ok  )

if it works ok ..... try

startx

---

### Post by indyrenegade on 2011-10-14
Okay, I entered sudo apt-get update, then it asked for my "[sudo] password" but I am unable to enter anything.

---

### Post by 23dornot23d on 2011-10-14
has it locked up ?

it may not display what you type ...... but it does accept it 

then press enter ......

or if that fails just try 

**startx**

---

### Post by indyrenegade on 2011-10-14
I connected my comp straight into my modem via Ethernet cable and entered the command. It appeared to work but after some text stating "hit" and "ign" it said..

    "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

Should I still try startx?

---

### Post by 23dornot23d on 2011-10-14
No

do the command

**sudo dpkg --configure -a**

it will continue from where it left off and fix the system .... hopefully

---

### Post by indyrenegade on 2011-10-14
Okay. I did it, and it ran a lot of set ups, though there was quite a few errors along the way, and now it reads.. 

    Setting up Ubuntu-desktop
    ldconfig deferred processing now taking place
    Processing triggers for initramfs-tools ...
    update-infinitramfs: Generating /boot/initrd.img-2.6.38-11-generic
    Errors were encountered while processing:
     erlang-inets
     erlang-mnesia
     erlang-runtime-tools
    eileen@eileen-laptop: ~$

---

### Post by 23dornot23d on 2011-10-14
Ok well although it had some errors it seems to have completed ok ....

lets just see if we can can get the last packages to install ok ....

try

apt-get install aptitude

aptitude safe-upgrade

( these are just to make sure your system is uptodate - after do startx )

or reboot if its successfull .....

---

### Post by indyrenegade on 2011-10-14
I tried both, they read that they couldn't open the lock file and that it was unable to lock the administration directory. Also, it asked if I was root.

---

### Post by 23dornot23d on 2011-10-14
sorry my fault needed sudo .... and it will ask you to enter your password .....

sudo apt-get install aptitude

sudo aptitude safe-upgrade

---

### Post by indyrenegade on 2011-10-14
Not a problem. I entered them, and they just got done going through a lot of updating. 
Now it reads.. 

    Current status: 0 broken [-31, 13 updates [-682],
    eileen@eileen-laptop:~$

---

### Post by 23dornot23d on 2011-10-14
ok try 
[B]
startx[/B]

---

### Post by indyrenegade on 2011-10-15
Sorry for the delay in response. It worked perfectly and I was brought to my new home screen. Thank you!

---

### Post by 23dornot23d on 2011-10-15
Nice one .... can you mark it as solved please ...... ;)

---

