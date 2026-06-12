---
title: "Force ubuntu to boot after power failure without user input"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by antoniospider on 2013-06-25
Hi people ! ;)
As the title says i've got a problem after booting operations , i want ubuntu starts normally without user input after a power failure.
I've followed different suggestions , the 2 ones were :

1) editing the  /etc/grub.d/00_header at the lines 283 and modify the  GRUB_RECORDFAIL_TIMEOUT from -1 wait forever to 0 thus do not show any message  if [ "${recordfail}" = 1 ]; then
  set timeout=0  <----edit this integer so that it is 0 [zero]
else
  set timeout=3
fi
--
the default for set timeout is -1 which of course is "wait forever"
=] 

2)The second one was to edit the etc/default/grub files and uncomment the line at " GRUB_DISABLE_RECOVERY"

Both those configurations are failed , i thought with the first solution i could solve the problem but the boot recovery page was there yet .

Could you please give me some help ?? thanks in advance ... antonio

---

### Post by antoniospider on 2013-06-25
i have ubuntu 13.04 64 bit

---

### Post by MidnightGrey on 2013-06-25
I dont think i've ever suffered a power failure myself, may i ask what happens normally after a powerfailure?

---

### Post by antoniospider on 2013-06-25
Hi MidnightGrey , i have a terminal with a linux ubuntu system and a player where runs some advertising , everything in a customer agency and i need the terminal stays alive every time even when there is a power failure. In that case ubuntu shows the grub page with some choice , depends on the SO you have installed in your hd , in my case ( i have just ubuntu installed) 2 choices "ubuntu" and "Advanced... " . If there is no one with a keyboards attached, it's not possible to go ahead because there isn't a countdown boot splash like in windows where there are 30 secs before it boots up the first choice in the list to boot

---

### Post by MidnightGrey on 2013-06-25
Hmm okay but does the PC stay on the GRUB menu after a normal reboot? 
(or does a power failure trigger a different set of GRUB settings is what i'm wondering).
Also after you edited 00_header and grub i'm assuming you did **sudo update-grub** to set changes.

---

### Post by MidnightGrey on 2013-06-25
can you also copy paste your /etc/default/grub for me.

---

### Post by antoniospider on 2013-06-25
Yes MidnightGrey !
No, after a normal reboot it goes up normally , just after a power failure it shows up something like this :
[IMG]http://buzzcodington.files.wordpress.com/2011/04/grub.jpg[/IMG]

without any possibility to enter in the system if not with a keyboard .
And as i remember , no , i havn't give the sudo aupdate-grub , i thought that saving the files with root permits and rebooting , the grub update automatically the information... i'm going to do it ;) 

Here the /etc/default/grub code ;)
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

thanks a lot 4 the support !

---

### Post by antoniospider on 2013-06-25
here the response of the update-grub command
```
sudo update-grubGenerating grub.cfg ...
/etc/grub.d/00_header: 281: /etc/grub.d/00_header: Bad substitution



```
i think the change made in the line hasn't produced the expected effect :)

---

### Post by antoniospider on 2013-06-25
this is the code i changed following the suggestion of an internet user 
```

if [ "\${recordfail}" = 1 ]; then
  set timeout=${GRUB_**_RECORDFAIL_TIMEOUT:0}**_
else
  set timeout=${2}
fi

```

---

### Post by MidnightGrey on 2013-06-25
> 
And as i remember , no , i havn't give the sudo aupdate-grub , i thought  that saving the files with root permits and rebooting , the grub update  automatically the information

so not exactly. The true config file is called grub.cfg, however it is recommended you do not edit that file directly as any incorrect statements in that file could cripple your GRUB preventing you from booting into anything. Therefor several script files were created as a frontend for users to customise (these files are the /etc/default/grub and 00_headers, among others). When you edit any of the script files you need to call "update-grub" to rebuild the grub.cfg file using your new changes.

Did you backup your 00_header? try to reset it to its' original state and call "sudo update-grub" again to see if that error goes away.

---

### Post by antoniospider on 2013-06-25
ok thanks 4 explanation , yes i did a back up of the file . so do i have to edit the grub.cfg to have expected effect ?

---

### Post by antoniospider on 2013-06-25
i found this line similar to the other one in the grub.cfg file : 
```

terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi

```

---

### Post by MidnightGrey on 2013-06-25
i wouldnt recommend editing grub.cfg unless you know what you're doing, also any time you call update-grub you will rebuild the grub.cfg from the scripts so you are better off finding out how to do it from the scripts instead.

---

### Post by MidnightGrey on 2013-06-25
Okay i think i found a solution to your problem; instead of editing 00_header you should create a custom script file like so:

1. Open a terminal
2. $ cd /etc/grub.d/
3. $ sudo gedit 02_kill_recordfail
4. copy paste this into it
```

#! /bin/sh 
set -e
function recordfail { 
#   save_env recordfail disabled    
    set recordfail=1 
} 
EOF

```
5. sudo chmod 755 02_kill_recordfail
6. sudo update-grub
Make note of the output and look for your new script "02_kill_recordfail"

edit:
you know what upon further investigation i believe this is wrong, if you've already done it you can revert changes by deleting the 02_kill_recordfail file and then doing 'sudo update-grub' again.
sorry...

---

### Post by antoniospider on 2013-06-25
oook :D , i followed those steps , it returns me this one when i execute the sudo grub-update command: 
```

visiontest@visiontest2:/etc/grub.d$ sudo update-grubGenerating grub.cfg ...
/etc/grub.d/02_kill_recordfail: 3: /etc/grub.d/02_kill_recordfail: function: not found

```
pratically now the function is disabled no ? thanks a lot

---

### Post by antoniospider on 2013-06-25
okok noo problem , i think the solution is very close to us :) ... i'm not so expert in scrpiting but i can understand bash

---

### Post by MidnightGrey on 2013-06-25
Okay! i've found it, the solution is surprisingly simple,
What version of Ubuntu are you running? This solution is for Ubuntu 12.04 or later.
you simply add this line to your /etc/default/grub
```

GRUB_RECORDFAIL_TIMEOUT = 0

```
You can replace the 0 with any number for a delay (in seconds).
and then do 'sudo update-grub' after changes.

There you go, lol

edit: this is assuming you're using the default 00_header and you didnt edit it.

---

### Post by antoniospider on 2013-06-25
I have UBUNTU 13.04 64 bit .
Yes the files are all in the original form , i tested all this change on another machine leaving the original one clear ;)
so... i made the change and here it is the response :
```

visiontest@visiontest2:/etc/grub.d$ sudo update-grub
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: GRUB_RECORDFAIL_TIMEOUT: not found

```
it seems it cannot recognize the function

---

### Post by MidnightGrey on 2013-06-25
Okay i just tested it (on 12.04)
its
```

GRUB_RECORDFAIL_TIMEOUT=0

```
not
```

GRUB_RECORDFAIL_TIMEOUT = 0

```

and it compiles without errors

---

### Post by antoniospider on 2013-06-25
ok thanks a lot really 4 the support !
i compile it and it returns me no error , now i'm going to test it and i will let you now if it boots automatically 
thanks a lot , have a nice day ;)

---

