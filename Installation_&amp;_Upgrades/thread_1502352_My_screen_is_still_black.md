---
title: "My screen is still black"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by filsdepapa on 2010-06-05
Hi
I have a destop which is an [COLOR=Blue]IBM ThinkCentre[/COLOR].  Recently I ran [COLOR=Blue]uburntu 9.10[/COLOR] but I have tried  to upgrade to[COLOR=Blue] 10.4 Lucid.[/COLOR] It took a week long  to download and another week to install. I don't remember after it  finished to install and asked me to do? Because it asked me there are  300 old files which are not compatible so what I need to do with them?  keep or remove? Unfortunately, I don't know in computer, and also for  the fear to loose Asterisk files, I click on "KEEP". Therefore, the  system continues to clean my folders and files...thus few minutes later,  my screen turned to black...and it's still black now. I forgot to  mention the screen when it downloaded to upgrade, the screen was black  too, but I didn't stop to RESTART EVERYDAY to make sure my PC is  working. 

NOW my screen is black. If I turn it on I get the grubs  as below:

[COLOR=#3333ff]uburntu 10.4 LTS, kernel  2.6.32-22 generic [/COLOR]
uburntu 10.4 LTS, kernel  2.6.32.22 generic (recovery)
uburntu 10.4 LTS, Kernel 2.6.31-21  generic
uburntu 10.4 LTS, kernel 2.6.31-21 generic (recovery)
uburntu 10.4 LTS, kernel 2.6.31-20    generic

same repeat as above.....2.6.31-20   generic  (recovery)
same.............................2.6.31-19 generic
same.............................2.6.31-19 generic (rec...)
same.............................2.6.31-18    gen.
same.............................2.6.31-18 gen..(rec)
same.............................2.6.31-17    gene.
same.............................2.6.31-17 gene.(rec.)
same.............................2.6.31-16    gene
same.............................2.6.31-16 gene (rec.)

Use the arrow (up) and (down) keys to select which entry is highlighted.  Press enter to boot the select OS, 'e' to edit the command before  booting, or 'c' for command-line.

If I don't choose any line above, then the line that is highlight is  automatically  the first line which is:
[COLOR=#3333ff]uburntu  10.4 LTS. kernel 2.6.32-22  generic[/COLOR]
If I do nothing , once time (seconds) is past over,  the  following  screen appears:

[COLOR=Red]Boot from (hdO,5) ext3   a09111ce-7ba2-491c-9996-eba033470de3
[/COLOR] [COLOR=Red]Starting up  ...[/COLOR]

NOW IF I CHOOSE  and pressing on "e" (editing) the line
[COLOR=Blue]uburntu  10.4 LTS, kernel2.6.32-22 generic[/COLOR]
I GET THESE CODES
[COLOR=Red]uuid   a09111ce-7ba2-491c-9996-eba033470de3
kernel   /boot/vmlinuz-2.6.32-22-generic  root=uuid=a09111ce-7ba2-491c-->
initrd    /boot/initrd.img-2.6.32-22-generic
quiet[/COLOR]

NOW IF I  HIGHLIGHT AND PRESS (E) ON THE LINE
[COLOR=Blue]uuid     a09111ce-7ba2-491c-9996-eba033470de3[/COLOR]
[COLOR=Black]**I  get the following message and codes**:[/COLOR]
[ Minimal BASH-like  line editing is supported. For the first word, TAB  lists possible  command completions. Anywhere else TAB lists possible  completions of a  device/filename. ESC at anytime to exit. ]

[COLOR=Red]grub  edit> uuid    a09111ce-7ba2-491c-9996-eba033470de3[/COLOR]

NOW  IF I HIGHLIGHT THE [COLOR=Blue]SECOND LINE [/COLOR]AND PRESS  (E)
[COLOR=Blue]kernel    /boot/vmlinuz-2.6.32-22-generic..........491c-->[/COLOR]
[COLOR=Blue]I get the following message and codes:[/COLOR]
[ Minimal BASH-like line editing is supported. For the first word, TAB   lists possible command completions. Anywhere else TAB lists possible   completions of a device/filename. ESC at anytime to exit. ]
[COLOR=Blue]
** [COLOR=Red]<e-7ba2-491c-9996-eba033470de3  ro quiet   splash[/COLOR]**[/COLOR]

Now  if I highlight the 3rd line and press on (e) that is:
[COLOR=Blue]initrd   /boot/initrd.img-2.6.32-22-generic[/COLOR]
What i  get?
[ Minimal BASH-like line editing is supported. For the first  word, TAB   lists possible command completions. Anywhere else TAB lists possible   completions of a device/filename. ESC at anytime to exit.  ]

[COLOR=Red]**grub edit> initrd   /boot/initrd.img-2.6.32-22-generic**[/COLOR]

After all, I  don't know what to do? My screen is still black even I  boot one of these kernels or grubs above.

Does anyone can help me  or give me any suggestion? I am appreciated. I have no knowledge in  computer. I understand I will go around if you give me just a little  detail. but better then nothing.

Thank  you.

---

### Post by dino99 on 2010-06-05
your grub menu looks good, no need to edit it, select recovery mode to boot, your problem seems to be due to graphic driver not activated

then after login, on the command line: 

sudo rm -f /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f  (accept the propositions)
sudo dpkg --configure -a

more info with the links below

---

### Post by filsdepapa on 2010-06-05
> **dino99 said:**
> your grub menu looks good, no need to edit it, select recovery mode to boot, your problem seems to be due to graphic driver not activated

then after login, on the command line: 

sudo rm -f /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f  (accept the propositions)
sudo dpkg --configure -a

more info with the links below

Hi,
Thanks for your reply. So now I select [COLOR=Blue]recovery mode[/COLOR] to boot and what I get now?
[COLOR=Blue]Recovery Menu[/COLOR]
[COLOR=Blue]                      clean       Try to make free space
                      dpkg        Repair broken packages
                      fallsafe     Run in fallsafe graphic mode
                      grub         Upgrate grub bootloader
                      netroot     Drop to root shell prompt with network
                      root          drop to root shell prompt[/COLOR]


     [COLOR=Red]'ok'[/COLOR]                      '[COLOR=Red]cancel[/COLOR]'

What do I do next, please? In addition, what's a graphic driver?

Thank you

---

### Post by filsdepapa on 2010-06-05
> **filsdepapa said:**
> Hi,
Thanks for your reply. So now I select [COLOR=Blue]recovery mode[/COLOR] to boot and what I get now?
[COLOR=Blue]Recovery Menu[/COLOR]
[COLOR=Blue]                      clean       Try to make free space
                      dpkg        Repair broken packages
                      fallsafe     Run in fallsafe graphic mode
                      grub         Upgrate grub bootloader
                      netroot     Drop to root shell prompt with network
                      root          drop to root shell prompt[/COLOR]


     [COLOR=Red]'ok'[/COLOR]                      '[COLOR=Red]cancel[/COLOR]'

What do I do next, please? In addition, what's a graphic driver?

Thank you

AFTER ALL, I press "enter" and BOOT THE LINE
[COLOR=Blue]dpkg Repair broken packages
[/COLOR]Now the screen is stopped at this point, it requires what? I don't know what to answer?
[COLOR=DarkOrange]Recovery Menu
[/COLOR] [COLOR=DarkOrange]                      [COLOR=RoyalBlue]clean       Try to make free  space
                      dpkg        Repair broken packages
                      fallsafe     Run in fallsafe graphic mode
                      grub         Upgrate grub bootloader
                      netroot     Drop to root shell prompt with network
                      root          drop to root shell prompt[/COLOR][/COLOR]

re-sysinit Star/running, process 15939
*Not starting internet superserver: no services enable
*Sttarting Fostfix Mail Transport Agent postfix
Starting fto server:Running:/usr/sbin/pure-ftpd-1pam -E -8 UTF -8 -u 1000 -0 clf: /var/log/pure-ftdp/ transfer log -B
[COLOR=Red]*[/COLOR]Scee ch-dispatcher configured for war sessions
*Starting the winbind daemon winbind
*Starting common unix Printing system: cupsd
[COLOR=Red]*[/COLOR]FulseAudio configured for per-user sessions
Enabling additional executable binary formats binfnt-support
*checking battery state...

Uburntu 10.4 LTS filsdemaman-destop tty1
filsdemaman-destop login:{B{B
Password:
login timeout after 60 seconds
uburntu 10.4 LTS filsdemaman-destop tty1


With the message above, anybody can help me please? If I type "enter" I'll get again 
Uburntu 10.4 LTS filsdemaman-destop tty1

Thanks

---

### Post by kansasnoob on 2010-06-09
After recovery mode completes choose failsafeX and see what happens. If that get's you a desktop we need to see the output from terminal of:

```
lspci | grep VGA
```

If failsafeX fails we still need to know the output of that command so use any Live CD or Live USB that will run on that machine to get that output.

That will give us specific graphics chip info. There are specific issues with various graphics chips:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Window%20corruption%20with%20older%20ATI%20graphics%20cards](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Window%20corruption%20with%20older%20ATI%20graphics%20cards)

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

But you must first know what graphics chip you have.

---

