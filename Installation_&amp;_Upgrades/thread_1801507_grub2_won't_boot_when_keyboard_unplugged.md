---
title: "grub2 won't boot when keyboard unplugged?"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by Celoxocis on 2011-07-10
before i posted this i made sure i googled and searched the ubuntu forums for the same problem but i was unable to find one! and slowly but surely this is getting on my nerves...

i build an customized NAS using this [supermicro board]("http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA-H-D525.cfm") and created an live-usb-stick with minimal natty (based on the minimal.iso 64bit) installed using expert command line as the nas will be running headless anyway.

as i use an chenbro case with 4hdd bay drives. my idea was to install the OS to an usb-disk, i was lucky i got one USB-pendrives still around.

so i installed an minimal-ubuntu, setup raid using mdadm, samba, etc. had the system reboot a few times everything worked perfectly fine. until i decided to remove the keyboard and the screen which i had used for the initial setup, just so that i could start the ssh-remote installer.

i went back to my rig and shutdown the system and sent an magic packet to my nas to test the WOL i had setup. checked with "ping nas" and nothing... so i went back to my nas and grub was just sitting there! only after plugging in the keyboard and rebooting the system grub would load the OS but not without the keyboard. the NAS itself it place in my livingroom so i gotta remove the keyboard for the WAF :P 

i can even reproduce this bug/feature everytime.
i never had this problem with my media-center which runs lucid and is also based on the lucid x64 iso.

my question:
is there any way i could debug grub? to find out why it's hanging. dmesg doesn't show me anything grub related. 
or could anyone point me in the right direction what could be causing this?

i was first thinking its the mb-bios. but it's not. i made sure the only boot device selected is the USB-pendrive. i also switched pendrives with the same result. so it must be grub!?

---

### Post by MAFoElffen on 2011-07-10
> **Celoxocis said:**
> before i posted this i made sure i googled and searched the ubuntu forums for the same problem but i was unable to find one! and slowly but surely this is getting on my nerves...

i build an customized NAS using this [supermicro board]("http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA-H-D525.cfm") and created an live-usb-stick with minimal natty (based on the minimal.iso 64bit) installed using expert command line as the nas will be running headless anyway.

as i use an chenbro case with 4hdd bay drives. my idea was to install the OS to an usb-disk, i was lucky i got one USB-pendrives still around.

so i installed an minimal-ubuntu, setup raid using mdadm, samba, etc. had the system reboot a few times everything worked perfectly fine. until i decided to remove the keyboard and the screen which i had used for the initial setup, just so that i could start the ssh-remote installer.

i went back to my rig and shutdown the system and sent an magic packet to my nas to test the WOL i had setup. checked with "ping nas" and nothing... so i went back to my nas and grub was just sitting there! only after plugging in the keyboard and rebooting the system grub would load the OS but not without the keyboard. the NAS itself it place in my livingroom so i gotta remove the keyboard for the WAF :P 

i can even reproduce this bug/feature everytime.
i never had this problem with my media-center which runs lucid and is also based on the lucid x64 iso.

my question:
is there any way i could debug grub? to find out why it's hanging. dmesg doesn't show me anything grub related. 
or could anyone point me in the right direction what could be causing this?

i was first thinking its the mb-bios. but it's not. i made sure the only boot device selected is the USB-pendrive. i also switched pendrives with the same result. so it must be grub!?
So the BIOS option is switched to "Ignore Keyboard Error On Startup" right?  In Grub, there is noting that will stop it on a keyboard error, that's why setting up a headless to tty is so easy with that.

On the other hand-  Xorg does...  Thats why most headless servers try to prevent  an Xstart... just a config thing to get past.  For what I think you are try to do, There is an option switch that you can add to xorg.conf > Section  "Serverflags" > Option "AllowMouseOpenFail" "true"... All the other config options are based on how and what you are using to connect remotely.  (Remote Xterm pass-through and such)

---

### Post by Celoxocis on 2011-07-10
i even set it to "ignore all errors on startup" in the bios.

i don't even use or have x-server installed. to manage the nas i use putty and ssh

is there a way for grub to printscreen it's log?

---

### Post by MAFoElffen on 2011-07-10
> **Celoxocis said:**
> i even set it to "ignore all errors on startup" in the bios.

i don't even use or have x-server installed. to manage the nas i use putty and ssh

is there a way for grub to printscreen it's log?
Heres what I want you to do:

Reboot> Press the shift ket repeatedly while it's booting to bring up the Grub Menu > Press "e"  to get it into Edit mode > Go down to the line that starts with  "linux" > delete the text " quiet splash vt.handoff=7 " and replace  it with " --verbose text " > press <cntrl><x> and boot...

It should boot into a test console using verbose boot messaging.  If it did boot, then it's not grub nor the kernel.  If it boots okay, then it will ask you for the username and password.

Tell me if you can get that far...

---

### Post by Celoxocis on 2011-07-11
thx! i will try when i get home but i'm not sure it will produce any useful info.
as long as i use the keyboard and the keyboard is plugged in, it never hangs on the grub screen. it will do so only when the keyboard is unplugged. i guess i could try unplugging the keyboard after hitting ctrl+x/f10 :-/

[edit]
ok i just got home and run through the --verbose text mode. i got all way to the login without any errors. so i did an "halt" and unplugged the keyboard just to see if i can reproduce the error again.
and i finally got some error from grub! don't know why i haven't seen that the first times... i guess the old lcd screen was just to slow

error: hd0 read error
error: hd0 read error
error: unknown terminal 'gfxterm'
error: no such partition error: no such partition  Failed to boot both default and fallback entries Press any key to continue...

it works perfectly fine when the keyboard is plugged and no the keyboard has no mbr or flash-device integrated :-/ it's one simple usb keyboard

---

### Post by MAFoElffen on 2011-07-11
> **Celoxocis said:**
> thx! i will try when i get home but i'm not sure it will produce any useful info.
as long as i use the keyboard and the keyboard is plugged in, it never hangs on the grub screen. it will do so only when the keyboard is unplugged. i guess i could try unplugging the keyboard after hitting ctrl+x/f10 :-/

[edit]
ok i just got home and run through the --verbose text mode. i got all way to the login without any errors. so i did an "halt" and unplugged the keyboard just to see if i can reproduce the error again.
and i finally got some error from grub! don't know why i haven't seen that the first times... i guess the old lcd screen was just to slow
```

error: hd0 read error
error: hd0 read error
error: unknown terminal 'gfxterm'
error: no such partition error: no such partition  Failed to boot both default and fallback entries Press any key to continue...

```it works perfectly fine when the keyboard is plugged and no the keyboard has no mbr or flash-device integrated :-/ it's one simply usb keyboard

Okay... trying to figure out how to reproduce this so you can have your keyboard disconnected and still have some control to diagnose this.

Open a terminal.  
```

sudo gedit /etc/grub.d/40_custom

```While GEdit is open, also open /boot/grub/grub.cfg... copy (fron  grub.cfg)and paste the menu item to the end of the  40_custom ... Including the 
```

Menu ...
...
}

```Go down to the kernel boot line and use the same grub menu kernel  boot line options: 
```

acpi_osi=Linux nomodeset --verbose text

```Change the Menu Item Title so that you can ID it easlly, Such as After where it says Ubuntu, add Text Console... Save and Exit. Then run update-grub to pick up those changes... What that did  was add a menu item so you can easily use it to get to text console mode.  

Reboot and select that menu item to make sure it works.

Install startup-manager and run it:
```

sudo apt-get install startup-manager
startup-manager

```Change to startup order, putting this a s the default for startup... That way you'll be able to start it with the keyboard disconnected.

After it boots, if it does boot, you should be able to connect a keyboard (connection picked up from the ACPI listener) and be able to supply input-- with the current boot and sys logs having caught any errors for the current session.  That way maybe we can get messages and error that aren't corrupted by disconnecting the keyboard at the grub menu(?)

When you get logged into the text console...
```

cp /var/log/boot.log ~/Documents/boot.log.error

```Which will make a copy of your boot log so the we can check what  errors are going on at boot... then the second will create a log of the  results of a ping to the Internet. Please post these new files... You'll  find them in your Documents directory.  I had you copy and create files   so you'll have access to that instance later.

In the meanwhile, I'm figuring out if it;s worth teaching you how to turn grub debugging mode on, how to describe to you how it's it done... Or if it's more trouble than the results it would provide...

---

### Post by MAFoElffen on 2011-07-11
> **MAFoElffen said:**
> 
In the meanwhile, I'm figuring out if it;s worth teaching you how to turn grub debugging mode on, how to describe to you how it's it done... Or if it's more trouble than the results it would provide...
Okay, the full debugging option is out to "share" how... It remote handling that would require me to compile a new version of grub for you wiht the debugging system, then explain to you how to connect to it remotely...

But there in an internal function of standard grub, that toggles what they call a basic "debug" function-- but what it really is-- Is like the "--verbose" function for the kernel / It turns on more verbose messaging during the grub functions.  It is a Grub command.  Now how to explain and how to use it...

Look at this:
```

menuentry 'Ubuntu Textt Console with Debug, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    [COLOR=Red]debug[/COLOR]
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root 32939def-1f4a-4134-9b56-bed2319a9216
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro [COLOR=RoyalBlue]acpi_osi=Linux nomodeset--verbose text[/COLOR]
    initrd    /boot/initrd.img-2.6.38-8-generic
}

```[COLOR=Red]That [/COLOR]should toggle it on during Grub's processes then, the [COLOR=RoyalBlue]kernel boot line[/COLOR] toggles on it's extra messages....

---

### Post by Celoxocis on 2011-07-11
ok i added the custom grub-menu entry including grup-update
but im not gone use startup-manager to change the boot order.
im just gone plug in my ps2-keyboard and unplug the usb-keyboard and select the custom entry. (same error happens with ps2-keyboard only plugged in)

ok this is weird.

after updating grub to accommodate the menu entrys i went to halt the system. unplugged the usb-keyboard and plugged in the ps2-keyboard. and after hitting "shift" the grub-menu came up but the custom-entry was not there.
so i manually edited with option "e" and included the the debug and the "kernel boot line" and hit F10.
```

error: hd0 read error
error: unknown terminal 'gfxterm'
error: no such partition
error: no such partition  Failed to boot both default and fallback entries Press any key to continue...

```i didn't check yet but i doubt anything was written into "/var/log/boot" as grub wasn't able to find the usb pendrive...

edit2:
plugged in the usb-keyboard and the menu-entry is there with everything else. boot was fine.

this is the out output of /var/log/boot after selecting the custom-menu-entry
```

fsck from util-linux-ng 2.17.2
/dev/sdc1: clean, 45469/62080 files, 182669/248320 blocks
 * Starting AppArmor profiles       ^[[128G
^[[122G[ OK ]

```and this is /var/log/boot:
```

(Nothing has been logged yet.)

```is this output normal?

edit3:
saw your boot_info_script and created an results.txt
maybe it will help somehow

---

### Post by MAFoElffen on 2011-07-11
> **Celoxocis said:**
> 
ok this is weird.

This is very weird!  

I just Emailed someone I feel is the most versed on GNU Grub that I know of, to ask him what he thinks.  He's usually watching another forum.  Hopefully he can look at this with a fresh perspective.

---

### Post by MAFoElffen on 2011-07-11
> **MAFoElffen said:**
> Edit--  Sorry.  It didn't even get as far as we did before it dead-end.Please post your current /etc/grub.d/40_custom file.  I'm going to see if I can add debugging symbols to it to break and trace though it... segment it down to diffrent areas of it's boot process.

Translation-  i'm going to make it stop in steps to see just where it gets the error.

---

### Post by drs305 on 2011-07-12
I am on the road and don't even have a USB keyboard to play with for troubleshooting purposes. I don't know at present what is triggering the problem.

There are two things to try. I believe the first one is more likely but provide a second one as a slight possibility.

1. The 30_os-prober script provides a keystatus check to interrupt a boot. If it is unable to determine the status, the boot stops at the menu to allow the user to make a selection.

Without a keyboard, the key press status is not determinable and that may be your issue. To check it, boot normally and disable 30_os-prober and update grub with the following commands:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
grep "keystatus" /boot/grub/grub.cfg
```

The last command should return no results, indicating the keystatus check is no longer part of the grub.cfg file. If the keystatus check is still found, manually edit /boot/grub/grub.cfg as in the example below and comment out the entire keystatus key section. 

Reboot without the keyboard connected and see what happens. If it doesn't work, make 30_os-prober executable and rerun 'sudo update-grub' to restore grub.cfg to the way it was.

2. This is less likely to work, but if #1 was unsuccessful it's something to try. You should probably rule out the 'recordfail' function of Grub 2 as the problem. The recordfail check forces Grub to stop at the menu and await user input. The intent is to allow the user the option of selecting an OS after a failed boot rather than continuously attempting a reboot with the same choice. With a server, this may not be a desired option.

Removing the check won't fix the underlying problem but it may mask it and allow the system to reboot in cases where the fault is not fatal.

To circumvent the recordfail check, boot and open grub.cfg for editing. Normally we don't edit this file directly since it is automatically rewritten when grub is updated, but for testing it will work as long as you don't run update-grub.```

gksu gedit /boot/grub/grub.cfg
```

Make the following change, save the file, but do NOT update Grub2.
> 
**#**if [ "${recordfail}" = 1 ]; then
**#**else
  set timeout=10
**#**fi

Reboot and see if the system will now boot successfully (perhaps on the second boot) or just continuously recycles.

---

### Post by MAFoElffen on 2011-07-13
@Celoxocis:

Haven't heard from you in a bit and wondering if it was because you hadn't heard from me (personally)?

I feel drs305 is the most versed person here with Grub.  I had asked him to come in on this to help.  Did what he suggested help you any?

I've been hovering on IRC #grub for the last 2 days trying to ask about this with no answers at all.  The only thing someone asked "me" about your problem was if the keyboard was PS2 pr USB... I said PS2... But truthfully, I couldn't find that answer in your posts.

While I was pondering if anyone there could shed any light on this... I did look back on 3 things that might help with this.

1. - Entering in grub's "debug" toggle into the start of 00_header and enter a bunch of "break" tags to step through the boot process.... Except, the only way that;s going to work without a keyboard (interaction needed to continue after a break) is to manually remove the preceding break to go on to the next process.

2. Compile grub with debuging symbols, install it and connect to it remotely... Letting it error and capturing the data... submitting it to Savannah (GNU Grub's Bug reporter).  That's pretty drastic for the average user in the way of a skillset.

3.  Recreating the problem here.  Either finding a work-around here or submitting the data to Savannah.  To do that, I'd need to know a little more about your hardware and what you are using for the OS and installed app's.  You listed some of the app's in post one... but didn't sy whether it was Desktop or Server.

---

### Post by MAFoElffen on 2011-07-13
[I]> **drs305 said:**
> To circumvent the recordfail check...
I also found another place where "recordfail" comes up in Grub2... at least in Ubuntu:
```
[FONT=monospace]
[/FONT]menuentry 'Ubuntu Text Console, with Linux 3.0-020639rc7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 [COLOR=Red]recordfail[/COLOR]
 set gfxpayload=$linux_gfx_mode
 insmod part_msdos
 insmod ext2
 set root='(/dev/sdc,msdos1)'
 search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
 linux    /boot/vmlinuz-3.0-020639rc7-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro [COLOR=Green]acpi_osi=Linux nomodeset --verbose text
[/COLOR] initrd    /boot/initrd.img-3.0-020639rc7-generic 
} 

```Where as all that the linux kernel needs to boot from Grub2 would be something such as this
```
[COLOR=purple]
[COLOR=Black]root (hd0,1) [/COLOR][/COLOR][COLOR=Black]
[COLOR=purple][COLOR=Black]kernel /vmlinuz root=/dev/hda2
boot[/COLOR] [/COLOR]
 [/COLOR]
```[/I]  [I]
...So commenting out the :"recordffail" line in the mneu item shouldn't stop it from booting, but might be something to try(?)
[/I]

---

### Post by drs305 on 2011-07-14
> **MAFoElffen said:**
> [I]
I also found another place where "recordfail" comes up in Grub2... at least in Ubuntu:

...So commenting out the :"recordffail" line in the mneu item shouldn't stop it from booting, but might be something to try(?)
[/I]

It would have the same effect, yes. 

The reason I prefer to just to change the timeout directly is that the 'recordfail' call is added to each menuentry. You could have multiple entries and would have to remove each one you planned on testing vs just changing the timeout once. But both methods ensure the timeout isn't set to -1.

---

### Post by Celoxocis on 2011-07-14
Sorry i was busy with work the last couple of days. I will have some time tomorrow after work and on weekend to do more testing! Thanks for the quick replys so far! Highly appreciated! :)

[edit]
Sorry for the confusion of usb-keyboard or ps2-keyboard. I tried both. The problem is that grub won't boot from the pendrive if the USB-Keyboard is Unplugged during the boot process (doesn't matter if its from halt to power-up or a simple restart and unplugged). I've also tried with an PS2-keyboard which had the same result as if i had no USB-Keyboard plugged.

Two days ago i did some try and error with an option in the Bios which allows me to select how many USB-Ports i want to activate. It goes from 2-to-12 USB ports in steps of two (default was 12). I tried to find which would be port1-port2 and so on. For testing i set it to "2 USB Ports" only in the bios and saved those and unplugged the USB-Keyboard. Grub was able to find the penrdrive/partition and to boot, the boot process went all the way till "mountall" and stalled there. My guess is that my raid-array config gets the wrong DEVICE numbering (mdadm.conf) as with 10 usb-ports less would change the sata drives from something like "sde->sdc" and so on. Which definitly is the reason for the stalling.

After this i wonder if it's really grub or if it's some Bios problem. But i kinda doubt it's the Bios, how else would grub be able to show-up if it can't find the pendrive, when grub itself is installed on the MBR of the pendrive, right? If it were not able to see the pendrive at all. I wouldn't have been able to see grub at all, right?

[edit2]
The board i'm using is the Supermicro [X7SPA-H-D525]("http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA-H-D525.cfm")
The enclosure jfyi (not relevant) [Chenbro ES34069]("http://usa.chenbro.com/corporatesite/products_detail.php?sku=79")

---

### Post by MAFoElffen on 2011-07-14
> **drs305 said:**
> It would have the same effect, yes. 

The reason I prefer to just to change the timeout directly is that the 'recordfail' call is added to each menuentry. You could have multiple entries and would have to remove each one you planned on testing vs just changing the timeout once. But both methods ensure the timeout isn't set to -1.
I see now... I now understand.  As I understood, he was getting to the menuitem, then...  I can see where that would take care of that.

I spent a day and a half on IRC #grub and no one shed any light on this. Was a little frustrating being on ignore there.  LOL   My only idea left was to change it from passing an error code to displaying a warning of the error status.

---

### Post by MAFoElffen on 2011-07-15
> **Celoxocis said:**
> Sorry i was busy with work the last couple of days. I will have some time tomorrow after work and on weekend to do more testing! Thanks for the quick replys so far! Highly appreciated! :)

[edit]
Sorry for the confusion of usb-keyboard or ps2-keyboard. I tried both. The problem is that grub won't boot from the pendrive if the USB-Keyboard is Unplugged during the boot process (doesn't matter if its from halt to power-up or a simple restart and unplugged). I've also tried with an PS2-keyboard which had the same result as if i had no USB-Keyboard plugged.

Two days ago i did some try and error with an option in the Bios which allows me to select how many USB-Ports i want to activate. It goes from 2-to-12 USB ports in steps of two (default was 12). I tried to find which would be port1-port2 and so on. For testing i set it to "2 USB Ports" only in the bios and saved those and unplugged the USB-Keyboard. Grub was able to find the penrdrive/partition and to boot, the boot process went all the way till "mountall" and stalled there. My guess is that my raid-array config gets the wrong DEVICE numbering (mdadm.conf) as with 10 usb-ports less would change the sata drives from something like "sde->sdc" and so on. Which definitly is the reason for the stalling.

After this i wonder if it's really grub or if it's some Bios problem. But i kinda doubt it's the Bios, how else would grub be able to show-up if it can't find the pendrive, when grub itself is installed on the MBR of the pendrive, right? If it were not able to see the pendrive at all. I wouldn't have been able to see grub at all, right?

[edit2]
The board i'm using is the Supermicro [X7SPA-H-D525]("http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA-H-D525.cfm")
The enclosure jfyi (not relevant) [Chenbro ES34069]("http://usa.chenbro.com/corporatesite/products_detail.php?sku=79")
Sorry, didn't see this until moments ago.

Let me get this straight... What you described was with changing the BIOS USB port descriptions  was changing the usb connected drive assginments?  So changing the drive assignment of your USB ports, even though it's booting from that USB drive would boot and see grub... but if the assigned drive description changed, then it would not see the drive-- ergo the cannot read hd0 error and then not booting.  Thinking out loud.  That sound like what is going on?

Only a portion of Grub is installed in the mbr of the pendrive.  It has pointers to the rest of grub that is installed in a /boot directory somewhere.  Default is the /boot directory of the Ubuntu installed system partition... unless you installed it elsewhere.  How do you have your system laid out... know part of it is RAID.

Did you try to edit the grub files like drs305 suggested?

---

### Post by krazyd on 2012-08-10
I just wanted to confirm the bug and workaround in this thread.

I have the exact same board, and the exact same issue. The solution is to enable only 10 usb ports rather than 12. Then grub will boot without the keyboard.

Weird bug. :-P

edit: oh yeah, i'm seeing this on debian wheezy.

---

