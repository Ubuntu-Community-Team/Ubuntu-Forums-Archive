---
title: "Dell XPS 15 + 17.10 vs. Touchpad (not working)"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by msbt on 2017-10-31
Hi there!
First of all thanks for the great support, I could find a lot of solutions here over the last years while only browsing. Now it's time for me to post since I ran into a problem I cannot solve on my own. I'm not sure if this is the right forum, might also be Hardware so please forgive me if it had to go there.

Lets get to it: I'm having troubles with Ubuntu 17.10 or rather with the touchpad of my brand new Dell XPS 15. 

Here's what happened so far: When I got the laptop a few weeks ago there was only Win 10 Pro installed. First thing I did was resize the Win partition (NVMe SSD) to make space for Mint (17.10 wasn't released yet) and installed it. Mint installer crashed when chosing the keyboard language and in the second attempt it (or rather me) deleted all (including Windows) partitions by accident. Good thing Ubuntu 17.10 got released shortly after that so I could try that. During that installation I was using legacy settings in bios, no touchpad was working during boot/setup, but after reboot everything was working (touchpad, webcam, wifi, even the 4k touchscreen), so basically everything you would need to work with it.

Few days later I changed back to UEFI and reinstalled Win 10 (wiped the whole disk again) and after all updates, reinstalled Ubuntu 17.10 aswell. 

Now here's my problem: Since then I can't get the friggin touchpad to work, everything else does, but it doesn't even show up in xinput since the change to uefi:

x@x-xps:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:13                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:13                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-touch:13                           id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:13                        id=8    [slave  keyboard (3)]

I installed both, xserver-xorg-input-libinput and xserver-xorg-input-synaptics, doesn't change anything. I even reinstalled 17.10, but that didn't help either.

tl;dr: 17.10 doesn't detect the touchpad of my xps 15 anymore

Anyone an idea what I might be missing here?

Best regards and thanks in advance,
M

---

### Post by msbt on 2017-10-31
Ok wow, I was playing around for days and just now (because it wouldn't shut down properly) I've edited grub with acpi=force with
sudo nano /etc/default/grub
and put in 
GRUB_CMDLINE_LINUX_DEFAULT="acpi=force"

After reboot the touchpad was working!

*edit* new xinput

x@x-xps:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=13    [slave  pointer  (2)]
&#9116;   &#8627; DLL07BE:01 06CB:7A13 Touchpad               id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD: Integrate             id=11    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=15    [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                    id=16    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=17    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=18    [slave  keyboard (3)]

So technically this can be closed again, but may be helpful for others if it stayed somewhere.

Best regards,
M

---

### Post by gtgrover on 2018-04-03
Thanks!  It worked for me too.

---

