---
title: "Keycodes,scancodes ,how to set them for keyboard backlit"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by cpu2007 on 2013-08-28
I have posted a topic some time ago about having problem with the fn keys on my laptop.
The problem is still there and it seems that no one has a solution.

Recently I came across scancodes,keycodes that are used to set keys actions that may very from manufacturer to manufacturer.

My keyboard backlight doesn't work. I have tried solutions online for samsung series 7 chronos but none of them worked.

Now what I did is create a new mapping and test it temporarily.
setting kbdillumdown,kbdillumup,kbdillumtoggle(i dont remember the right words but I know i spelled them right in the mapping), I set them to F9,F10,F11 .
Before, when pressing F9,F10,F11 nothing would happen but now when I press them, I see the keyboard backlight logo on the top right of the screen. The problem is the bar is always full(even if the backlight on the keyboard is not on) and regardless of whether i bright it down,up or toggle, the same logo with full bar appears, suggesting that no changing is being made.

What could be the problem here?

Thanks

---

### Post by tgalati4 on 2013-08-28
Does the backlight work now and it is just the icon that is not working correctly?

---

### Post by cpu2007 on 2013-08-28
No, it doesn't work, it does react to the press of the F9-F10  buttons(which it wasn't previously) by showing the backlight keyboard  logo on the screen; however the keyboard light doesn't light up.

---

### Post by cpu2007 on 2013-08-29
any advice?

---

### Post by tgalati4 on 2013-08-29
You will have to send an email to Samsung asking for a Linux module to activate the keyboard backlight.  Post their response.  I need some humor today.

In the meantime, button events are normally located in /proc/acpi so look in there and post anything related to extra function keys.  

```
ls /proc/acpi/button
```

I have an old Thinkpad T43p and there are a lot of linux utilities to get the extra buttons to work:

tgalati4@Mint14-Extensa ~ $ apt-cache search thinkpad
martian-modem - ltmodem alternative driver providing support for Agere WinModem
martian-modem-source - Source for the martian-modem driver
acpitool - command line ACPI client
acpitool-dbg - command line ACPI client (debug)
gkrellm-thinkbat - ThinkPad laptops battery status indicator for GKrellM
hdapsd - HDAPS daemon for IBM/Lenovo ThinkPads and Apple iBooks/PowerBooks
kopete-plugin-thinklight - thinkpad flashing for kopete
pidgin-blinklight - Blinks your ThinkPad's ThinkLight upon new messages
thinkfan - simple and lightweight fan control program
tp-smapi-dkms - ThinkPad hardware/firmware access modules source - dkms version
tp-smapi-source - ThinkPad hardware/firmware access modules source
tpb - program to use the IBM ThinkPad(tm) special keys
xfce4-goodies - enhancements for the Xfce4 Desktop Environment


Samsung?  Not so much.

tgalati4@Mint14-Extensa ~ $ apt-cache search samsung
printer-driver-splix - Driver for Samsung and Xerox SPL2 and SPLc laser printers
bitpim - utility to communicate with many CDMA phones
bitpim-lib - architecture-dependent helper files for BitPim
madwimax - user-space driver for mWiMAX equipment based on Samsung CMC-730
pkpgcounter - computes number of pages or quantity of ink needed to print documents
skyeye - Embedded Hardware Simulation

Install *acpitool* and do a dump and see if there are any switches.

Open a terminal:

```
sudo apt-get install acpitool
acpitool -e
```

---

### Post by cpu2007 on 2013-08-30
Their reply was that they can't assist me with this issue as the drivers they have for the fn keys only work on windows.
They advised to look on linux forums to see if there's any solution as this is an open source system.

---

### Post by tgalati4 on 2013-08-30
Extra keys tend to be controlled by the BIOS and ACPI.  Look through the scripts in /etc/acpi and /etc/acpi/events.  If you find an event or script related to the keyboard backlight, then you need to put in the appropriate command.

---

### Post by cpu2007 on 2013-09-04
I found the backlight up and down events but by the names of the events in there, there's no reference to samsung(the laptop I have); some are called asus,panasonic etc.
THis is the list:

```
ls /etc/acpi/events/
ac                            lenovo-touchpad    tosh-lock
asus-f8sv-touchpad            lenovo-touchpad2   tosh-mail
asus-keyboard-backlight-down  lenovo-undock      tosh-media
asus-keyboard-backlight-up    lidbtn             tosh-next
asus-media-eject              panasonic-lockbtn  tosh-play
asus-rotate                   powerbtn           tosh-prev
asus-touchpad                 sleepbtn           tosh-stop
asus-video                    thinkpad-cmos      tosh-wireless
asus-wireless-off             thinkpad-radiosw   tosh-www
asus-wireless-on              tosh-battery       videobtn
battery                       tosh-hibernate
ibm-wireless                  tosh-ibutton


```

Inside the asus  keyboard-up for example I find this

```
# /etc/acpi/events/asus-keyboard-backlight-up
# This is called when the user presses the key brightness 
# up button and calls /etc/acpi/asus-keyboard-backlight.sh for
# further processing.

event=hotkey ATKD 000000c4
action=/etc/acpi/asus-keyboard-backlight.sh up
```

How can I use the info that I have here to set my samsung laptop?

---

### Post by tgalati4 on 2013-09-04
So, you are getting closer.  If you know which hotkey is pressed--presumably Fn-F9 and Fn-F10, then put the appropriate code for that key into the scripts and it might work.

Post the output of:

```
cat /etc/acpi/asus-keyboard-backlight.sh
```

As you can see there is a two-part action that takes place:

1.  A hotkey is detected by the BIOS or ACPI based on the hexidecimal keycode of the Fn-F9 or F10 key pressed.  This key then runs an action specified by action=.

2.  Whatever is in the action script will be called.  Probably an echo function to put a value into a system device.

So you need to find out what the hex value is for the Fn-F9 or F10 key is and then you need to modify the script that is called to make the keyboard backlight go up and down.

The other way to do it (and I don't recommend this, unless you know what you are doing) is to modify your keyboard mapping file:

```
cat /usr/share/acpi-support/key-constants
```

Near the bottom of the file you will see:

.
.
KEY_CONNECT=218
KEY_FINANCE=219
KEY_SPORT=220
KEY_SHOP=221
KEY_ALTERASE=222
KEY_CANCEL=223
KEY_BRIGHTNESSDOWN=224
KEY_BRIGHTNESSUP=225

Use *xev* to determine what keycodes show up when you hit Fn-F9 or Fn-F10.  If that number is not 224 or 225 then you need to change the file to reflect the correct keycodes.  If the keycodes don't show up while using *xev*, then they are intercepted by the BIOS/ACPI and you need to continue to use the script method stated first.

Send an email to Samsung asking for the keycodes for those keys.

One other place to check:  /sys/devices/platform/dell-laptop/backlight/dell_backlight

Look for any samsung files in /sys/devices/platform.

---

### Post by cpu2007 on 2013-09-05
The following is the content of asus-keyboard-backlight.sh
```

cat /etc/acpi/asus-keyboard-backlight.sh #!/bin/sh

# this directory is a symlink on my machine:
KEYS_DIR=/sys/class/leds/asus\:\:kbd_backlight

test -d $KEYS_DIR || exit 0

MIN=0
MAX=$(cat $KEYS_DIR/max_brightness)
VAL=$(cat $KEYS_DIR/brightness)

if [ "$1" = down ]; then
    VAL=$((VAL-1))
else
    VAL=$((VAL+1))
fi

if [ "$VAL" -lt $MIN ]; then
    VAL=$MIN
elif [ "$VAL" -gt $MAX ]; then
    VAL=$MAX
fi

echo $VAL > $KEYS_DIR/brightness

```
I'm a bit confused on the results that are returned by the command "xev", I am posting them now and I hope you can tell me what I need from there.
I believe the one we're interersted in are the one with F9 - F10 present it them.
```

PropertyNotify event, serial 40, synthetic NO, window 0x4400001,
    atom 0x1be (_NET_WM_ICON_GEOMETRY), time 10240939, state PropertyNewValue

KeyPress event, serial 41, synthetic NO, window 0x4400001,
    root 0x9b, subw 0x0, time 10242030, (4,-11), root:(70,41),
    state 0x0, keycode 75 (keysym 0xffc6, F9), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x4400001,
    root 0x9b, subw 0x0, time 10242170, (4,-11), root:(70,41),
    state 0x0, keycode 75 (keysym 0xffc6, F9), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 41, synthetic NO, window 0x4400001,
    root 0x9b, subw 0x0, time 10242961, (4,-11), root:(70,41),
    state 0x0, keycode 76 (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x4400001,
    root 0x9b, subw 0x0, time 10243162, (4,-11), root:(70,41),
    state 0x0, keycode 76 (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

ClientMessage event, serial 41, synthetic YES, window 0x4400001,
    message_type 0x130 (WM_PROTOCOLS), format 32, message 0x12e (WM_DELETE_WINDOW)


```

I'm also including the showkey -a output(in case it has info that might help)

I'm getting the output only when pressing F9 but not when pressing F10 
```

^[[20~      27 0033 0x1b
      91 0133 0x5b
      50 0062 0x32
      48 0060 0x30
     126 0176 0x7e

```

In addition I wanted to tell that the keys I'm pressing are just F9,F10, however shouldn't I be looking for a key combination FN+F10, FN+F9 ?

I didn't find the name of dell or any other device in the directory you've mentioned 
Here's the output:
```

ls /sys/devices/platform/
alarmtimer  Fixed MDIO bus.0  pcspkr     regulatory.0  vboxdrv.0
coretemp.0  i8042             power      serial8250
efifb.0     microcode         reg-dummy  uevent

```

PS: what type of numbers are the one shown in the backlight-script:
```
000000c5
```
Are they hex,dec? how do I convert them in their respective decimale or other type of values?

---

### Post by tgalati4 on 2013-09-05
Bring up calculator and View-->Programming.  That brings up a programming calculator with Hex to Dec conversion.  c5 is 197.  

Does your laptop have a Fn key?  On my thinkpad, I have blue markings on some of my function keys that are activated by pressing Fn-F5--which turns off wireless for instance.

Typically F1 through F12 are reserved for application quick-keys.  So extra laptop functions are handled with a Function-F-key.

---

### Post by cpu2007 on 2013-09-06
yes it does have an fn key. when I use the other keys f2,f3,f4 etc. I have to use them in combination with fn . so for example to get the screen brightness up i use fn+f4, fn+f3 for screen brightness down, similar for volume. However some keys don't work, keyboard backlight,wireless and fan toggle. I wanted to start with the keyboard backlight (I really need it) and then see if I can adjust the others as well

---

### Post by tgalati4 on 2013-09-06
So, you need to use *xev*.  Run it and place the mouse cursor in the *xev* box.  Type a few regular keys:  a s d f, and you will see keycodes show up in the terminal.  Then start typing your Fn keys.  The ones that don't show up are ones that are captured by BIOS/ACPI and hidden to the X-server.  Any function keys that do show up, note the keycode and use the Keyboard Preferences and assign shortcuts to those keys.  You can write a script to turn wireless on and off, turn on fans, lights, just about anything.  

So, if you can see the keys in *xev* then you can assign shortcuts.  If you can't see the keys in *xev*, then you need to use the ACPI framework, which consists of modifying the scripts that you looked at earlier with the correct keycodes.  This takes some trial and error.

---

### Post by cpu2007 on 2013-09-06
Sorry, your explanations are great and I do understand the logic behind it but I'm confused on how to put all of this into practical.
In one of my previous posts I've posted the results of the xev command,which are as follow for F9 and F10:

```

KeyRelease event, serial 41, synthetic NO, window 0x4600001,
    root 0x9b, subw 0x4600002, time 1187461, (38,47), root:(828,99),
    state 0x0, keycode 75 (keysym 0xffc6, F9), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 41, synthetic NO, window 0x4600001,
    root 0x9b, subw 0x4600002, time 1188081, (38,47), root:(828,99),
    state 0x0, keycode 76 (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


```

When pressing the fn key,while the xev command was running, I didn't get any result, does that mean that this is picked up by the bios or acpi right?

What I did next is change the asus_brightnessup and down file by changing the values in it with 
000000c7(for brightness up) and 000000c6 (for brightness down); I thought these are the values tham I'm looking for as they are in the xev results.
Have I done this right?

It didn't work, I don't really know where to go from here.

---

### Post by tgalati4 on 2013-09-06
You are getting closer.  The reason the asus_brightness script doesn't work is because you don't have a module loaded into memory that watches for those keys.

So, leave the keyboard brightness alone for now.  What other keys are you trying to activate?  Let's get one thing working at a time.  

First the basics, what modules are you running?

```
lsmod
```

I'm running on a Dell Inspiron 600m and it show the following:

tgalati4@Dell600m-mint14 ~ $ lsmod
Module                  Size  Used by
vesafb                 13478  1 
arc4                   12474  2 
joydev                 17162  0 
snd_intel8x0           33107  2 
snd_ac97_codec        105652  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                80235  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
**dell_laptop**            17162  0 
snd_seq_midi_event     14476  1 snd_seq_midi
dcdbas                 14055  1 dell_laptop
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   347496  0 
microcode              18210  0 
snd                    62146  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                825498  0 
pcmcia                 39545  0 
mac80211              461261  1 b43
psmouse                89579  0 
cfg80211              175574  2 b43,mac80211
soundcore              14600  1 snd
video                  18895  0 
snd_page_alloc         14037  2 snd_intel8x0,snd_pcm
ttm                    75535  1 radeon
serio_raw              13032  0 
drm_kms_helper         47304  1 radeon
bcma                   34484  1 b43
rfcomm                 37277  0 
yenta_socket           27096  0 
pcmcia_rsrc            18192  1 yenta_socket
bnep                   17708  2 
parport_pc             31969  0 
drm                   239022  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
mac_hid                13038  0 
ppdev                  12818  0 
bluetooth             183310  10 rfcomm,bnep
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
binfmt_misc            17261  1 
lpc_ich                16926  0 
shpchp                 32190  0 
p4_clockmod            12829  0 
i8k                    13909  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
ssb                    50294  1 b43

So, I have a module that is named *dell_laptop* and it probably has to do with special functions on dell laptops.   To find out if this module has any special switches:

```
modinfo dell_laptop
```

tgalati4@Dell600m-mint14 ~ $ modinfo dell_laptop
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/platform/x86/dell-laptop.ko
license:        GPL
description:    Dell laptop driver
author:         Matthew Garrett <mjg@redhat.com>
srcversion:     F3778843864566B6FA396E8
alias:          dmi*:svn*DellComputerCorporation*:ct*8*:
alias:          dmi*:svn*DellInc.*:ct*9*:
alias:          dmi*:svn*DellInc.*:ct*8*:
depends:        dcdbas
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 686 

So no switches, but it does give a location of where the modules are located:

tgalati4@Dell600m-mint14 /lib/modules/3.5.0-39-generic/kernel/drivers/platform/x86 $ ls
acerhdf.ko       classmate-laptop.ko  fujitsu-laptop.ko  intel_ips.ko           msi-wmi.ko           thinkpad_acpi.ko
acer-wmi.ko      compal-laptop.ko     fujitsu-tablet.ko  intel_menlow.ko        mxm-wmi.ko           topstar-laptop.ko
amilo-rfkill.ko  dell-laptop.ko       hdaps.ko           intel_mid_powerbtn.ko  panasonic-laptop.ko  toshiba_acpi.ko
apple-gmux.ko    dell-wmi-aio.ko      hp_accel.ko        intel_mid_thermal.ko   samsung-laptop.ko    toshiba_bluetooth.ko
asus-laptop.ko   dell-wmi.ko          hp-wmi.ko          intel_oaktrail.ko      samsung-q10.ko       wmi.ko
asus-nb-wmi.ko   eeepc-laptop.ko      ibm_rtl.ko         intel_scu_ipcutil.ko   sony-laptop.ko       xo15-ebook.ko
asus-wmi.ko      eeepc-wmi.ko         ideapad-laptop.ko  msi-laptop.ko          tc1100-wmi.ko

So you can see a samsung module.

tgalati4@Dell600m-mint14 /lib/modules/3.5.0-39-generic/kernel/drivers/platform/x86 $ modinfo samsung-laptop
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/platform/x86/samsung-laptop.ko
license:        GPL
description:    Samsung Backlight driver
author:         Greg Kroah-Hartman <gregkh@suse.de>
srcversion:     FFB59C04A71D56CEEE3ACD6
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*N250P*:rn*N250P*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*N250P*:rn*N250P*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*NF110/NF210/NF310*:rn*NF110/NF210/NF310*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*N150/N210/N220*:rn*N150/N210/N220*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*N145P/N250P/N260P*:rn*N145P/N250P/N260P*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*N150P*:rn*N150P*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:ct*14*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:ct*10*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:ct*9*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:ct*8*:
depends:        video
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 686 
parm:           force:Disable the DMI check and forces the driver to be loaded (bool)
parm:           debug:Debug enabled or not (bool)

Unfortunately, this seems to only control the screen backlight.  

I did find this post:  [http://askubuntu.com/questions/233312/how-to-make-keyboard-backlight-fn-buttons-work-in-samsung-series-9](http://askubuntu.com/questions/233312/how-to-make-keyboard-backlight-fn-buttons-work-in-samsung-series-9)

Other folks are having problems on Win8 which were fixed by a BIOS flash.  So I would suggest updating your BIOS to the latest.

Try some of these things:  [https://help.ubuntu.com/community/SamsungSeries9#FnKeys](https://help.ubuntu.com/community/SamsungSeries9#FnKeys)

---

### Post by cpu2007 on 2013-09-15
Sorry for the late reply, I was trying to follow the instruction and make it work.

lsmod didn't give me anything useful so I decided to follow the instructions on the links you've provided. What I got in lsmod was as follow 
```

Module                  Size  Used by
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
bbswitch               13611  0 
btusb                  22474  0 
nvram                  14362  0 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
snd_hda_codec_hdmi     36906  1 
bluetooth             228667  12 bnep,btusb,rfcomm
snd_hda_codec_realtek    78399  1 
binfmt_misc            17500  1 
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
arc4                   12615  2 
snd_hda_intel          39619  5 
snd_hda_codec         136498  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
iwldvm                241872  0 
mac80211              606457  1 iwldvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
microcode              22881  0 
iwlwifi               173516  1 iwldvm
i915                  600349  3 
lpc_ich                17061  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
psmouse                95905  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13215  0 
snd_timer              29425  2 snd_pcm,snd_seq
drm_kms_helper         49394  1 i915
snd                    68876  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   286028  4 i915,drm_kms_helper
mei                    41158  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
nls_iso8859_1          12713  1 
video                  19390  1 i915
wmi                    19070  0 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
ahci                   25731  4 
libahci                31364  1 ahci
r8169                  67466  0 


```


After following the instructions on the link you've provided, I get the logo of the screen keyboard brightness,which stays always to full but the keyboard doesn't lit up.
Even using alt+F4 for some reasons doesn't work(to close windows, folders etc)
Here's the keymapping:


```

0xCE prog1              
0x89 brightnessdown   
0x88 brightnessup
0x82 switchvideomode
0xF9 f23
0xA0 mute
0xAE volumedown
0xB0 volumeup
0x97 kbdillumdown
0x96 kbdillumup
0xB3 prog3
0xD5 wlan

```

As you can see from the pic below, when I press FN+F9 or FN+F10, I get the same logo of the keyboard with full bar (ignore the fan logo)
[IMG][[IMG]http://s23.postimg.org/w7ovmbvdz/Screenshot_from_2013_09_15_23_31_55.jpg[/IMG]]("http://postimg.org/image/w7ovmbvdz/")[/IMG]


Any advice on what I'm doing wrong here?
plus, is it possible to update the bios without having windows installed?

---

