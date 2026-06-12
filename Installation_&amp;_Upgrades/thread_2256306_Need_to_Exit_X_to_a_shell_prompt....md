---
title: "Need to Exit X to a shell prompt..."
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by Vizhon on 2014-12-11
I know this question has been fielded before and have found said posts and knowledge base entries but none of them seem to work for me... Running Ubuntu 14.04, yes, I can 'sudo stop lightdm' to exit X, but that doesn't bring me to a shell prompt. Instead that leaves me on a blank black screen with no interface at all and I can't go on to install drivers like I need to do when I am looking at a blank screen, so I will once again raise the question on here, "How do I exit X to a command prompt?" because it seems to change every few versions and it has clearly changed since all the answers I've found.

I'd actually prefer it to not boot into X at all, but to boot into a BASH shell and let me manually launch X when I want to use it.

---

### Post by Lars Noodén on 2014-12-11
You can get to a console by pressing ctrl-alt-f1.  The same goes for f2 through f6 to get other consoles if you need them.  Then when you want to go back to X you can press ctrl-alt-f7  Or are you wishing to not have X at all until you need it?

---

### Post by Vizhon on 2014-12-11
I need to shut down X, completely. I need to install NVidia drivers to get my second monitor working, and Nvidia will not install if X is running, so I need to, just like I said, EXIT X and get to a shell prompt... I don't want a command line within X or a term window within X.. I need a shell prompt with no X.

PS: I do not see where the confusion in exiting X is... Heck, I don't get why I get a lot of nonsensical answers when I post requests for help on forums but it happens almost without fail... People type in abreviations and give almost no info and people seem to know what the hell they are asking and when I type in complete sentences and am very clear about what I am asking people never seem to understand the question until I have restated it a half dozen times and always, I was perfectly clear on the first time if people actually read what I typed.... EXIT... I said right in the topic EXIT.. Not get to a command prompt within X and besides, if I can't get to a command prompt in X, how the hell would be I be doing 'sudo shutdown lightdm'? to know it is dropping me to a blank screen instead of a command prompt.

ALSO: I have tried doing a reset to get to the reboot menu and get to the command prompt that way but for some reason that menu does not recognize my USB keyboard and the only key that seems to work on my PS2 keyboard is the enter key, so I it doesn't understand the "C" key to get to the command prompt, the arrow keys to scroll throught the menu options or anything else other than just selecting whatever option it's decided to default to by hitting return.

PPS: having tried Ctrl+Alt+F1, I find that it also goes to a blank, black screen and does not give me a prompt, so it would seem the issue to solve here is why my command prompt doesn't work at all.

---

### Post by Bashing-om on 2014-12-11
Vizhon; Hello;

I will try and address your issues;
1) > 
ALSO: I have tried doing a reset to get to the reboot menu and get to the command prompt that way but for some reason that menu does not recognize my USB keyboard and the only key that seems to work on my PS2 keyboard is the enter key, 

Which keyboard do you intend to use ? Bios hands off to grub which configuration to expect ( then grub hands off to the operating system) . In bios set the corresponding setting(s) And, plug and play is enabled.

2) > 
I'd actually prefer it to not boot into X at all, but to boot into a BASH shell and let me manually launch X when I want to use it.

Once bios is set for the keyboard in use one can edit the '/etc/default/grub' file to effect booting to terminal:
Edit the line GRUB_"CMDLINE_LINUX_DEFAULT="
to:
```

GRUB_CMDLINE_LINUX_DEFAULT="text"

```
EDIT: Forgotten step:
For the change to propagate; issue terminal command:
```

sudo update-grub

```
Now, depending on the Desktop Environment, to start the GUI from the booted terminal - for instance here unity (lightdm) - issue the terminal command:
```

sudo service lightdm start

```

3) > I need to shut down X, completely. I need to install NVidia drivers to get my second monitor working, and Nvidia will not install if X is running, so I need to, just like I said, EXIT X and get to a shell prompt... I don't want a command line within X or a term window within X.. I need a shell prompt with no X.

To stop X ( again my reference is unity as the DE ) obtain a console interface with key combo ctl+alt+F2 ( because X might be  running in F1, and the command line will not be available). In the F2 interface issue terminal command:
```

sudo service lightdm stop

```
At this point X is stopped, and the terminal is available to install the drivers.

My bit to try and help. Please to advise where I can assist further.

1st thing remains to get that keyboard recognized.
[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2014-12-11
I'm sorry. But I hesitate to tell the OP to make a permanent change, that they will have to undo later... until they've exhaust other methods. Besides, what you told them will not work without the missing step you omitted. His grub menu will not update those changes until you tell it too. (You left that step out)

To the OP. Got to the second post my sticky- Link in my sig line. In that post is many links. Follow the one to edit to temporarily edit the Grub Memu to boot into Text mode as console text mode (single user)... If for some reason you cannot get to the Grub menu, use the links in that second post to force the Grub 2 display or stay displayed.

If you need a tutorial or help on installing nvidia, bogan kept up with updating those tutorials for those. He was good at document the quirks of our testing of that with Ubuntu. Search on his posts in that thread and go backwards form current. Unfortunately, the forums software was changed and we lost the ability to update links on old posts. Some of the early posts are dated. The admin staff wanted me to convert that whole thing as a Wiki, but never got any help with that so...

So in the first page of my sticky, in the hot-key refrence, where it said that to kill-X, use <cntrl><alt><backspace>? That chaged in Ubuntu 12.04 to <alt><printscreen><k>... but like the OP found out, the vitirtual tty, which the standard TTY xccosole is... will be tweaked on some cards until he installs the driver. So along with "S" in the kernel boot line, use "nomodeset".

---

### Post by Bashing-om on 2014-12-11
@ MAFoElffen; Thanks;

For protecting my back.
@ Vizhon;
+1 ^^ .


[INDENT][INDENT]we are here to help
[/INDENT][/INDENT]

---

### Post by Vizhon on 2014-12-11
Figured out how to setup GRUB to launch to a command prompt and will be setting up batch files to make it a single command to make the changes and reboot. This solved my problem with getting drivers installed and that is accomplished, but I still have the problem that dropping down to a command prompt instead of opening a terminal window in X gives me a blank screen, but I found in a brief search that I am not alone in that problem either and has something to do with the .bashrc file being setup wrong, but I'll worry about fixing the issue later.

I will say one thing that I never thought I'd say.. After fighting with Ubuntu all night long and finding almost nothing intuitive about it (when easy installation and intuitive interfaces I thought was the whole point), I am really missing the old Slackware, mush custom compile a kernel for your system, days, because frankly, it was easier and quicker to deal with and configure than trying to fix a one size fits all graphical installation that doesn't fit quite right.

Another issue I seem to be having that is driving me nuts is that every other boot starts up with Grub, whether I reset to it or properly shut down.

---

### Post by Bashing-om on 2014-12-11
Vizhon; Good .

Things are working out.
> 
 After fighting with Ubuntu all night long and finding almost nothing intuitive about it (when easy installation and intuitive interfaces I thought was the whole point), I am really missing the old Slackware, mush custom compile a kernel for your system, days, because frankly, it was easier and quicker to deal with and configure than trying to fix a one size fits all graphical installation that doesn't fit quite right.

Agreed, one size does not fit all. Sometimes one has to do a bit of tweaking. The good thing is that the tweaking can be done. In a bit of time, one knows what one wants from all the choices available. At that point in time, one can build exactly what they want for an operating system. Give it some time and bit of effort.

As to:
> 
Another issue I seem to be having that is driving me nuts is that every other boot starts up with Grub, whether I reset to it or properly shut down.

That happens if grub has any problem booting. It will present you with the grub boot menu. IF the original issue of this thread had been addressed, how 'bout closing this thread and open a new one for this grub issue ? That will have the better chance of getting the attention of those qualified in the boot process to address the issue. In this new thread include:
```

cat /etc/default grub
ls -al /etc/grub.d
cat /boot/grub/grub.cfg

```

Threads are like dead men, one to the box. Helps keep the forum sane.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MAFoElffen on 2014-12-11
On my main management console I have an NVidia GTX9800, using a 24" monitor with a corrupt EDID... It was tweaking with switching over to virt tty consoles. I have the animated Ubuntu Sun as my splash, To get both straighten out, well... Here is how I have mine in the /etc/default/grub file...

set the line Bashing-om sugested to:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesa:mode_option=1600x1200-32,mtrr=3,scroll=ywrap,noedid"

```
You would change the resolution with your resolution and leave out "noedid"

Same file, when you get down to the virt tty resolution, be sure to match the res to what you set above:
```

GRUB_GFXMODE==1600x1200x32

```

What you will need to do to update grub.cfg to pick up those changes is to:
```

sudo update-grub

```
Those things are still up-to-date and true from post one of that sticky... Try those and see if they help.

I have to add similar with my servers. I use KMS switches to an HP TFT5600 RKM rack mount console... that is tweaking about being probed for video modes. Server console is VGA graphical (not true text mode), so I set all of them in those same 2 lines of that file. But usually for them, just turn off KMS and set the tty console resolution. For example, here is from one of those servers:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=7
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0"
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
GRUB_GFXMODE=1024x768x16

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

```
... I have 2-3 work-arounds to turn that Grahical console mode off to straight text-mode... But I like the custom VGA palettes I use in tyy console. Looking at straight text is boring and hard to pick things out. But my servers also have minimum X installed for my management utils, so that config also helps with tty to X to tty on those.

Yes. I didn't mean any offense at all by my previous post. I'm easy going. We are all here to help [COLOR=#008080]each[/COLOR] other. I've been doing UNIX and XServer since 1988 and I still need help from time to time. There are 100 ways to do the same thing. But sometimes it's hard to pick one tree out of a forest. LOL. I too sometimes get tunnel vision, focused on what I think is wrong.

And as I've tried to explain in my sticky, and why it contained so many areas of things... Since 11.04 and the implementation of KMS, the graphics layer is affected by many things-- Grub2, through Kernel, through XServer, through the individual device drivers (and hardware). Hard to address just one area with that and say it's a separate issue, apart from all else.

---

