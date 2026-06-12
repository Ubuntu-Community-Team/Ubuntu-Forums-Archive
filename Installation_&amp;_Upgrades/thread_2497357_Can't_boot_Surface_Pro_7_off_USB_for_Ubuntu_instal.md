---
title: "Can't boot Surface Pro 7 off USB for Ubuntu install"
date: 2024-05-02
forum: Installation &amp; Upgrades
---

### Post by torontoguy on 2024-05-02
[SIZE=2][FONT=arial][COLOR=#333333]Hi all.[/COLOR]

[COLOR=#333333]I've got a Surface Pro 7 that's getting a bit long in the tooth. I've read that various Linux distros run well on it. Ubuntu in particular has quite a 
few detailed set-up guides. So I decided to give it a shot.[/COLOR]

[COLOR=#333333]The problem is, the Surface won't boot from a USB key.  The UEFI/BIOS is set to boot from USB first, before anything else. I've tried:[/COLOR]

[COLOR=#333333]-- 5 different USB keys (various sizes (apparently 64GB don't work) from 32GB down to 8)[/COLOR]
[COLOR=#333333]-- writing the Ubuntu ISO to the key using balenaEtcher, Rufus, and the dd command from a command prompt in a Linux virtual machine.[/COLOR]
[COLOR=#333333]-- setting the security setting in the Surface's UEFI/BIOS to off and third party (not Microsoft Only)[/COLOR]
[COLOR=#333333]-- turned off all other boot devices, so that it ONLY tries booting from the USB[/COLOR]
[COLOR=#333333]-- openSUSE Tumbleweed instead of Ubuntu[/COLOR]
[COLOR=#333333]-- Windows 11 (for poops and giggles, just to see) instead of Linux[/COLOR]
[COLOR=#333333]-- turned on the Surface normally, and while holding the down volume button.

[/COLOR]I've searched, to no avail, various Ubuntu, Linux, and MS Surface threads for tips. Including a detailed post on git 
called "Linux Surface." Lots of useful stuff. None of them, however, addressed a Surface NOT booting off USB. They
all assume that that part's a given.

[COLOR=#333333]Nothing works. It just sits there with the white Surface/Windows logo on a black screen, like it's mockingly judging me, until I eventually 
turn it off. I've left it like that for as long as an hour, just to see if the thing would figure out what I wanted it do do.

[/COLOR][COLOR=#333333]How on earth to I get the thing to actually boot off USB and into the Ubuntu installer?

[/COLOR][COLOR=#333333](a copy of this post was also posted on Microsoft's Surface support forum, but I'm not sure if I'm expecting anything)[/COLOR][/FONT][/SIZE]

---

### Post by tea for one on 2024-05-02
Ministry of Guesswork responding:-

Access UEFI settings
Disable Secure Boot
Disable TPM
Disable other security settings (if they exist)

---

### Post by gezzer2 on 2024-05-02
try restarting windows while holding the shift key. hold shift key and then click restart.
this will restart windows in recovery mode.

choose boot from other devises .. highlight the USB drive and press enter.

this should bypass the normal/standard boot restrictions ..

---

### Post by torontoguy on 2024-05-14
Hey. Thanks for the reply...  Unfortunately, if you reread my original post, I've already tried all those things. Or as many of them as exist. The UEFI security settings, and UEFI settings in general on the Surface Pro 7 are rather limited. So it's not hard to go through them.

---

### Post by torontoguy on 2024-05-14
Yup. Tried that already, too. Forgot to mention it in my original post, maybe? Whhen I go that route, it just sits there with a Windows/Surface logo on the screen, doing nothing, until I eventually power it off. The record is 20 minutes.

The weird thing is that I installed Ubuntu on this thing about a year ago, but went back to Windows because the instructions I found at the time for getting Ubuntu working properly on the thing were a hot mess.

So this SHOULD be possible. It's driving me nuts.

---

### Post by yancek on 2024-05-15
Did you try the various methods to boot from USB referred to at the microsoft site at the link below?  If so, what happens?

>  
The weird thing is that I installed Ubuntu on this thing about a year ago

Your notes from that install are no help?

---

### Post by ubfan1 on 2024-05-15
Some notes I was putting together to get to get the boot order and settings.

Machine Specific Problems Getting into UEFI Settings and the UEFI boot Menu

This section has nothing to do with Ubuntu, but there may be problems simply
getting into your machine's UEFI Settings or selecting a USB to boot.  Since
every machine is different, consider the following an outline of things to
try to gain control of your machine.

Getting to the UEFI Settings (formerly known as BIOS) or to the UEFI boot menu
(select a device or OS to boot) should be some machine specific key at
power-up (described below). When this does not work, try these suggestions.

Ensure the Windows Fast Start (some Windows power option) is off. This
settings may be pretty well hidden in the Windows Settings. Older Windows may
have the Settings/Power Options page with an "enable all settings" and
"advanced settings" to bring up the necessary checkoff button to turn off Fast
Start. For Windows 11 23h2, it is easier to start the Control Panel (type in
"control panel" in the run/search bar), then select the System/Security
section and then select the Power Options -- again enable all the controls,
then the Fast Start will show if it is checked off. When not "enabled", the
checkoff does not show, so you might think Fast Start is off when it is on.
Windows may reset this when it updates, so you might need to periodically turn
off Fast Boot again.

Check the UEFI Settings (f2,...) for a "Fast Boot" (select "normal", not
"fast") or a time to alter to give yourself enough time to acutally type the
UEFI Settings or Menu key. If this is already set to "fast" it may be tricky
to get into the UEFI Settings to change it. Hold the (F2 ?) key down on power
up, or type it repeatedly. If that fails, try shutting Windows down by holding
Shift, then use the "restart" selection from the power button. A screen should
offer you the option to run UEFI Settings.

Setting the boot order should be possible from the UEFI settings, but some
vendors may require you to set a password to access that function. Some
vendors may require to you set "Trust" on the Ubuntu bootloaders (grubx64.efi
or shimx64.efi).

Some machines may have a UEFI Setting which controls how a function key is
interpreted (do you have to hold down another FN key to enable the F2 key).

The Boot order may change when USBs are removed or changed. Windows may be
moved up to the first postion when this happens. Windows itself may change the
Boot order. Sometimes the USB needs to be present at shutdown to be made
available as a boot option at power up. After a change, it may be necessary to
make a full shutdown before reboot to make the changes permanent. Some
machines have a two level boot order: First level might be :"USB
CD/DVD.USBhdd,hdd, network" and the second level might be for "UEFI hard
disks" (which might just include the USB hdd and put it last). 

Ubuntu offers efibootmgr, which should be able to change UEFI boot order, but
some machines require such changes to be made only in UEFI Settings.

---

### Post by currentshaft on 2024-05-15
once a week anti-acid

---

