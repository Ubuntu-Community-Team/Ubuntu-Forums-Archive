---
title: "Can't stop at grub menu"
date: 2020-09-02
forum: Installation &amp; Upgrades
---

### Post by geckojames on 2020-09-02
Environment:

On a Dell xps 15 9560 machine, Ubuntu 20.04.01 was just installed on the second drive on the machine. The first drive was already installed opensuse, which has been running well for a few years.

The second drive on which ubuntu is installed was formatted and had nothing on it prior to installation. opensuse has nothing to do with it.

The installation uses UEFI and secure boot enabled, since both opensuse and ubuntu support them.

The installation finishes fine except that grub couldn't even show upon booting ubuntu, with three lines on the screen only:
1. press f1 to retry booting
2. press f2 to reboot to boot menu
3. press f3 to reboot to setup

I went to the Dell bios setup and manually added a boot entry which chooses the correct shim.efi file on the other drive (different from the original installation generated drive option), then ubuntu could boot fine.

However my actual problem is:

The boot only flashes the grub menu and does not stop.
I have already tried holding/repeatedly pressing the following buttons:
arrow key/space bar/shift/esc/e (maybe some other keys I find on the internet suggestions),
but the grub menu (blue background with text) only flashes and can't be stopped.

Since I could boot into ubuntu, I also checked the /etc/default/grub.cfg and noticed that [FONT=monospace]GRUB_TIMEOUT_STYLE[/FONT] was set "hidden", so I changed it to "menu", according to 
[https://www.gnu.org/software/grub/manual/grub/grub.html#Simple-configuration](https://www.gnu.org/software/grub/manual/grub/grub.html#Simple-configuration)

I also changed the timeout to either "2" or "-1".  (edit: and used the "update-grub" command)

Nontheless, all these do not change anything. The grub menu only flashes and can't be stopped.

---

### Post by kc1di on 2020-09-02
Change the grub time out to 5 or 10.  That should slow it up enough to let you make choices. 
Of course don't forget to issue the sudo update-grub command after saving the changes.

---

### Post by geckojames on 2020-09-02
> **kc1di said:**
> Change the grub time out to 5 or 10. That should slow it up enough to let you make choices. 
Of course don't forget to issue the sudo update-grub command after saving the changes.

> **geckojames said:**
> Environment:

Since I could boot into ubuntu, I also checked the /etc/default/grub.cfg and noticed that [FONT=monospace]GRUB_TIMEOUT_STYLE[/FONT] was set "hidden", so I changed it to "menu", according to 
[https://www.gnu.org/software/grub/manual/grub/grub.html#Simple-configuration](https://www.gnu.org/software/grub/manual/grub/grub.html#Simple-configuration)

I also changed the timeout to either "2" or "-1".  (edit: and used the "update-grub" command)

Nontheless, all these do not change anything. The grub menu only flashes and can't be stopped.

I don't think it's related to the grub options anymore, since making timeout value "-1", meaning waiting indefinitely didn't help. Besides interruption keys don't work in any case either.

---

### Post by Dennis N on 2020-09-02
In Ubuntu 20.04 default for /etc/default/grub contains:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
Change to:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
Grub_Timeout should be > 0.
In terminal, run **sudo update-grub**
Reboot and Grub menu will appear.

---

### Post by oldfred on 2020-09-02
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by geckojames on 2020-09-03
> **Dennis N said:**
> In Ubuntu 20.04 default for /etc/default/grub contains:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
Change to:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
Grub_Timeout should be > 0.
In terminal, run **sudo update-grub**
Reboot and Grub menu will appear.

Thank you. Surprisingly it works. 
However I notice that pressing "down arrow" or "spacebar" actually skips the grub menu. But if you wait a second on the grub menu screen "down arrow" works as a selection key.
Any suggestion on which key is safe to press to safely stop grub timeout counting?

---

### Post by tea for one on 2020-09-03
> **geckojames said:**
> Any suggestion on which key is safe to press to safely stop grub timeout counting?

Once the grub menu is displayed, down arrow will also stop the timer, then you can choose your selection with both up and down arrows.

(I think space bar and up arrow will also pause the timeout)

I find a 10 second Timeout is more comfortable.

---

### Post by geckojames on 2020-09-03
I seem to understand better the issue:

update-grub only works for one grub but I have two working grub for this ubuntu installation:
One is under FS0:\EFI\boot\bootx64.efi, the other is under FS1:\EFI\ubuntu\shimx64.efi.

update-grub only updates the latter but not the former. If I boot into the former ubuntu, the grub menu is not stoppable (I presume it still uses [COLOR=#000000][FONT=&amp]GRUB_TIMEOUT_STYLE=hidden)
[/FONT][/COLOR]I wonder which /etc/default/grub controls the former grub, and which efi should I choose to be the default boot entry, which can be configured in the BIOS setup.

edit2: exchange former<->latter

---

### Post by geckojames on 2020-09-03
I actually have no idea which efi is configured by /etc/default/grub now, since I find that either of them can have the unstoppable grub menu issue.

Under FS0:EFI, I have the following directories:  Dell, boot, opensuse. (under boot it has bootx64.efi and fallback.efi.)
Under FS1:EFI, I have the following directories: ubuntu, (under which there are grubx64.efi, shimx64.efi, mmx64.efi, BOOTX64.CSV, grub.cfg)
                                                                     BOOT (under which there are BOOTX64.EFI, fbx64.efi, mmx64.efi)
I know that ubuntu is installed on the second drive. Now which efi should I choose and stick to so that the grub menu would listen to the /etc/default/grub change???

---

### Post by oldfred on 2020-09-03
I think one grub is OpenSuse  and other is Ubuntu. But do not know if OpenSuse uses grub.

The bootx64.efi is often called the fallback and is just a copy of shimx64.efi (or Windows .efi file). It looks like OpenSuse creates a fallback.efi also.

If you post the link to a report from Boot-Repair you can see all the details.

---

### Post by geckojames on 2020-09-04
Does ubuntu reset grub on each shutdown/boot?
I find that the issue is that after changing "/etc/default/grub" and issuing "update-grub", grub menu can stop after the reboot.
But,
If I shut the pc down, and boot again, the boot menu will not be stoppable again. The updated grub has been ignored, despite the fact that my edit in "/etc/default/grub" stayed the way I made it.

Boot-repair seems to share to much info than necessary.
Ubuntu seems to be generating a grub disregard what's in /etc/default/grub

---

### Post by Dennis N on 2020-09-04
> Does ubuntu reset grub on each shutdown/boot?
No it doesn't.

The only time settings in /etc/default/grub would change is when grub itself is upgraded with a new version, or reinstalled. That doesn't happen very often. 

Don't confuse upgrading the grub package with what happens when **update-grub** is run. **sudo update-grub** only regenerates the grub menu based on the settings in /etc/default/grub and scripts in /etc/grub.d.

---

### Post by Dennis N on 2020-09-04
> I find that the issue is that after changing "/etc/default/grub" and issuing "update-grub", grub menu can stop after the reboot.
But, If I shut the pc down, and boot again, the boot menu will not be stoppable again.

I assume that by 'can stop' you mean 'does stop'? Like every time you reboot?

Reboot and power-off/power-on should act the same way as to grub menu display settings and content. I don't see an explanation at the moment for the different behavior. IF the menu also failed to display after a reboot, then booting Ubuntu through grub of another OS would be an explanation.  

Note: A technical detail - the computer doesn't read /etc/default/grub when you boot up or reboot. All those settings were incorporated into /boot/grub/grub.cfg when you used the command sudo update-grub. It is actually this file which is read on each boot or reboot to get menu settings and content.

Perhaps one of the experts on this forum will offer an explanation.

---

### Post by geckojames on 2020-09-04
I have boot the machine like 20 times already today to research the behavior of the grub menu shown/hidden. So I was wrong, there's no difference of rebooting/PC shutdown-boot. 
In fact, today  the grub menu can't show and stay (but only flash), although in /etc/default/grub the style has been set as "menu" and the timeout time is 10 (no change after the change I made yesterday).
Even if I do "update-grub", grub menu can't show.

I tried to use boot-repair, I seem to understand why my grub keeps becoming broken. Because even the boot-repair utility suggested to put my /boot and /EFI partition on /dev/sda (the first drive where opensuse is installed), but ubuntu is installed on /dev/nvmen1 (my second drive).

[B]In short, ubuntu wants its grub to be on the first drive /dev/sda, but I installed it on the second drive /dev/nvmen0. So ubuntu somehow ignores its grub on the second drive /dev/nvmen0, and somehow mysteriously uses its own grub hidden in somewhere, or in the EFI partition that I don't understand. So my "update-grub" changed a grub which ubuntu doesn't care.
I hope there's way to let ubuntu to not see the first drive at all.

[/B]p.s. During all this time opensuse's grub hasn't been affected, fortunately.

---

### Post by geckojames on 2020-09-04
But yesterday update-grub worked a few times, making me believe that the issue has been solved. Today, grub menu becomes hidden again.

---

### Post by Dennis N on 2020-09-04
I'm not sure how you are choosing which OS to use. In post #1, I you have F2 to open a boot menu. Is that it? Then, in post #8, you mention FS0 and FS1 - what are those?

---

### Post by tea for one on 2020-09-04
I am also not sure what you wish to achieve.

Do you want to keep both systems completely independent and choose the OS via the boot menu (F2 according to post 1, although I have also seen F12)?

Alternatively, do you want one OS to control the boot selection via grub?

As a point of interest, the last OS installed will generally take control of grub (which is probably what has happened)

---

### Post by geckojames on 2020-09-04
> **tea for one said:**
> I am also not sure what you wish to achieve.

Do you want to keep both systems completely independent and choose the OS via the boot menu (F2 according to post 1, although I have also seen F12)?

Alternatively, do you want one OS to control the boot selection via grub?

As a point of interest, the last OS installed will generally take control of grub (which is probably what has happened)

I wouldn't mind that one grub menu can control both opensuse and ubuntu. But it seems not the case at the moment, since opensuse's grub doesn't include ubuntu entry and vice-versa. So I'm currently booting using the machine's native boot menu (F12 for Dell), and I'm OK with it.

Opensuse boots from its own efi directory /boot/EFI/leap/shim.efi. It does not try to make itself in /boot/EFI/boot/*** so it doesn't affect other OSes.

As for ubuntu its EFI partition resides on /dev/nvmen0p1, and it does contain /EFI/ubuntu/shimx64.efi, but _*I feel*_ it wants something to do with the first drive.

That all being said, the problem I'm having is that:

Ubuntu's grub menu screen is hidden from time to time. I have not found the patterns for when boot menu is gonna be hidden/shown, although I'm using the same boot entry in the Dell's F12 boot menu entry, and /etc/default/grub has been set to show grub menu screen as always. There's no explanation why grub menu screen is hidden after a random number of boots. No I didn't update the ubuntu system during these boots. Sometimes I do update-grub to try to force ubuntu to show the grub menu screen, sometimes it works, sometimes it doesn't. /etc/default/grub has always been the same (set to show grub menu screen), but ubuntu would throw a dice to decide whether it wants to show it or not in the next boot.

**My current goal is very simple: to make the grub menu screen shown, all the time.**

---

### Post by geckojames on 2020-09-04
I have tried to use the boot-repair utility from a live ubuntu session. By default it suggested that the EFI and boot be on /dev/sda (my first drive where opensuse is installed), so I changed it to the second drive /dev/nvmen0 to continue. The repair utility seemed to proceed fine but in the end it said there was an error and asked me to send an email to ***@gmail.com

---

### Post by tea for one on 2020-09-04
Does the grub menu for opensuse appear every time you choose it?

If it does, then you may consider adding an Ubuntu entry to the opensuse grub?

---

### Post by Dennis N on 2020-09-05
> **tea for one said:**
> Does the grub menu for opensuse appear every time you choose it? If it does, then you may consider adding an Ubuntu entry to the opensuse grub?

+1 to doing this **&#8593;**

Grub menus with menu entries for 2 or more OS automatically pause at the menu when you start the computer, regardless of what you have set for GRUB_TIMEOUT_STYLE. I am just wondering why Ubuntu's OS prober didn't add one to the menu when you ran sudo update-grub. It should have if the other disk was connected at the time.

---

### Post by geckojames on 2020-09-05
> **tea for one said:**
> Does the grub menu for opensuse appear every time you choose it?

If it does, then you may consider adding an Ubuntu entry to the opensuse grub?

Yes, grub for opensuse works perfectly.

I actually used opensuse to include another OS boot entry before. Normally it has a tool called Yast2-bootloader. When you run it, it probes for other OSes and adds it to its grub entry.

Strangely, opensuse couldn't pick up ubuntu's boot entry this time.

---

### Post by tea for one on 2020-09-05
> **geckojames said:**
> Yes, grub for opensuse works perfectly.

I actually used opensuse to include another OS boot entry before. Normally it has a tool called Yast2-bootloader. When you run it, it probes for other OSes and adds it to its grub entry.

Strangely, opensuse couldn't pick up ubuntu's boot entry this time.

Well, this thread is providing some unexpected details, but we battle on with some suggestions.

In a nutshell, Opensuse doesn't pick up Ubuntu and Ubuntu doesn't pick up Opensuse.
Together with unusual grub behaviour in Ubuntu.

Can you shut down the PC and power off. Then boot into your UEFI set up screens and alter some settings:-

[LIST]
[*]Uncheck Secure Boot
[*]Uncheck Fast Boot (if checked) - somewhere in Boot > Boot Configuration as a guess.
[*]Deactivate your SSD (where you have opensuse) or physically unplug the drive.
[*]Save the settings
[*]Boot into Ubuntu
[*]Open a terminal and run **sudo update-grub**.
[/LIST]

Reboot and see if the grub menu appears with the previous 10 second timer?

---

### Post by geckojames on 2020-09-06
I claim to be the first to discover this mysterious behavior of random hidden/shown grub menu.

Findings:
Ubuntu needs to be placed on the top of the boot sequence so that its grub should act as what's been told in the grub option. Otherwise its grub menu would be hidden.
I noticed that opensuse however doesn't care if it's on top. I even tried to generate new grub for opensuse when it had boot not on top of the boot sequence to see if it would break opensuse's grub. It didn't.

What I still don't understand is though: ubuntu should either boot according to the grub options or not boot at all. But when it's unhappy about its boot entry position it decides to boot but not show its grub menu (using some other boot config hidden somewhere?)
Does this behavior lead to security issue?

---

### Post by tea for one on 2020-09-06
> **geckojames said:**
> I claim to be the first to discover this mysterious behavior of random hidden/shown grub menu.

Congratulations

You’ll have to wait a day or two for the hidden Grub Committee to verify your discovery.
That will put you on top of the leaderboard in the Ubuntu/OpenSuse division. ;)

Out of curiosity, can you put a bit of meat on the bone:-

[LIST]
[*]Your reference to boot sequence, I assume you mean the UEFI set up?
[*]Ubuntu grub now appears with a working timeout and including an entry for openSuse?
[*]OpenSuse grub is displayed with an entry for Ubuntu?
[*]
[/LIST]

Security issue? - That’s a very broad question and I think you should start a new thread in the relevant forum.

Cheers

---

### Post by geckojames on 2020-09-06
> **tea for one said:**
> Congratulations

You’ll have to wait a day or two for the hidden Grub Committee to verify your discovery.
That will put you on top of the leaderboard in the Ubuntu/OpenSuse division. ;)

Out of curiosity, can you put a bit of meat on the bone:-

[LIST]
[*]Your reference to boot sequence, I assume you mean the UEFI set up?
[*]Ubuntu grub now appears with a working timeout and including an entry for openSuse?
[*]OpenSuse grub is displayed with an entry for Ubuntu?
[/LIST]

Security issue? - That’s a very broad question and I think you should start a new thread in the relevant forum.

Cheers
It is the UEFI boot sequence;Two OSes can't see each other, which I am fine with.

---

