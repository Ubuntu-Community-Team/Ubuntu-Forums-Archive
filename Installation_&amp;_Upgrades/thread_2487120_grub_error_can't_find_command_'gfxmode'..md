---
title: "grub error: can't find command 'gfxmode'."
date: 2023-05-23
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-05-23
I've made a customized grub menu by placing all entries in the file */etc/grub.d/06_custom.  *

The grub menu now appears exactly as I want it, **IF** turn off the executable bit for both of the* 10_linux *and 30_*os-prober* files.

 But when I turn off the *10_linux* file (to get rid of menu-entries I don't want), I get[I]:

"error: can't find command 'gfxmode' Press any key to continue..." [/I]when I boot the top entry. 

If I turn *10_linux* back on, I don't get the error message, but a few extraneous menu-entries, that i don't want, appear in the grub menu.

Do I need to copy some of the code from *10_linux* into *06_custom*?  

What might be causing the error?

  ```

  1 #
  2 # If you change this file, run 'sudo update-grub' afterwards to update /boot/grub/grub.cfg.
  3 # For full documentation of the options in this file, see:
  4 #   info -f grub -n 'Simple configuration'
  5  
  6 GRUB_DEFAULT="0"
  7 GRUB_TIMEOUT_STYLE="menu"
  8 GRUB_TIMEOUT="10"
  9 GRUB_RECORDFAIL_TIMEOUT="10"
 10 GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
 11 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 12 GRUB_CMDLINE_LINUX=""
 13 GRUB_BACKGROUND="/home/rj/Pictures/do_not_move/pic-4-grub.jpg"
 14  
 15 # The resolution used on graphical terminal.
 16 # Note that you can use only modes which your graphic card supports via VBE.
 17 # You can see them in real GRUB with the command `vbeinfo' or 'videoinfo'.
 18 GRUB_GFXMODE="2560x1600x32,1920x1080x32,auto"
 19  
 20 # For a more readable font on high dpi screens, generated with:
 21 # sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono40.pf2 --size=40 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
 22 # per <https://blog.wxm.be/2014/08/29/increase-font-in-grub-for-high-dpi.html>
 23 GRUB_FONT="/boot/grub/fonts/DejaVuSansMono40.pf2"
 24  
 25 # The OS_prober feature is disabled by default in GRUB 2.06, which is the version included in
 26 # Ubuntu 22.04. This is an upstream change designed to counter potential security issues with
 27 # the OS-detecting feature (it mounts partitions to check for other OSes, this could be taken
 28 # advantage of, etc).  See:
 29 # <https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix>
 30 GRUB_DISABLE_OS_PROBER="false"
```
(The rest of the file is commented-out, but I don't think the settings in this file have much to do with the problem.)

---

### Post by #&amp;thj^% on 2023-05-23
Try with "GRUB_GFXMODE=auto" only, providing that's the file in question
Dang forgot this one as well
```
# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep
```
and to be clear:
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `videoinfo'
GRUB_GFXMODE=auto
```

---

### Post by watchpocket on 2023-05-23
Thanks for the suggestion but this didn't get rid of the error message.  
There must be something in the *10_linux* file about *gfxmode* that I need to put in *06_custom*.

---

### Post by MAFoElffen on 2023-05-23
LMFAO!!!

This is why:
```

mafoelffen@Mikes-B460M:~$ grep 'function gfxmode' /etc/grub.d/10_linux
function gfxmode {

```
The function for 'gfxmode' is defined in /etc/grub.d/10_linux. You disabled the execution bit on that script, so GRUB_GFXMODE is not defined. Make that script executable again and that error will go away...

Quote: *"It's okay. I saw this work once in a cartoon..."*

---

### Post by watchpocket on 2023-05-23
No, I get unwanted entries in the grub menu when I make 10_linux executable, as stated in my original post.

---

### Post by MAFoElffen on 2023-05-24
Not sure what entries you want to hide... For me, to skip something, I edit /etc/default/grub and add the line:
```

GRUB_OS_PROBER_SKIP_LIST="<UUID><PATH-TO-EFI_FILE>"

```
in my case that would be 
```

GRUB_OS_PROBER_SKIP_LIST="0150-726C@/efi/Microsoft/Boot/bootmgfw.efi" 

```

*** But looking at and tracing through the code in /etc/grub.d/10_linux, I suspect if you uncomment this line in your /etc/default/grub file
```

#GRUB_DISABLE_RECOVERY="true"

```
Add this line
```

GRUB_DISABLE_SUBMENU="true"

```
and change line #408 in file /etc/grub.d/10_linux from this
```

is_top_level=true

```
To this
```

is_top_level=false

```
That it will stop creating any menuentries from that script. That would toggle all the if statements that create menuentries to false.

EDIT-- And still have the logic there to write the gfxmode define interactively to grub.cfg...

---

### Post by watchpocket on 2023-05-24
> **MAFoElffen said:**
> Not sure what entries you want to hide...

I want to hide the two default entries that say "Ubuntu" and "Advanced Options for Ubuntu". 

Those are the only two default menu-entries left that display if I leave executable *ON* for 10_linux, and with the executable* OFF* for 30_os-prober. 

(To recap: if I turn *OFF* executable for both the 10_linux and 30_os-prober scripts, my menu is exactly as I want it, but that's when I get the *"can't find command gfxmode"* error.)

I have made all the menu entries I want in /etc/grub.d/06_custom.

> For me, to skip something, I edit /etc/default/grub and add the line:
```

GRUB_OS_PROBER_SKIP_LIST="<UUID><PATH-TO-EFI_FILE>"

```
in my case that would be 
```
in the terminal when I ran sudo update-grub
GRUB_OS_PROBER_SKIP_LIST="0150-726C@/efi/Microsoft/Boot/bootmgfw.efi" 

```

Where do I find the UUID and path-to-efi-file for those two default menu entries? (Likely somewhere in /etc/grub.d/10_linux, but where?)

I made all your suggestions below, ran *sudo update grub*, and got the same *'unable to find command gfxmode'* error message in grub when I selected to boot the top menu entry. (This of course is with 10_linux executable* ON*.)

But in addition I got an error message in the terminal when I ran *sudo update-grub* -- about line 451 of the .cfg file.  I could find nothing wrong with that line in 10_linux (but then I don't know what to look for):

```
451     initrd="${initrd_early} ${initrd_real}"
```

None of the below worked, but thank you for the suggestions.
> *** But looking at and tracing through the code in /etc/grub.d/10_linux, I suspect if you uncomment this line in your /etc/default/grub file
```

#GRUB_DISABLE_RECOVERY="true"

```
Add this line
```

GRUB_DISABLE_SUBMENU="true"

```
and change line #408 in file /etc/grub.d/10_linux from this
```

is_top_level=true

```
To this
```

is_top_level=false

```
That it will stop creating any menuentries from that script. That would toggle all the if statements that create menuentries to false.

EDIT-- And still have the logic there to write the gfxmode define interactively to grub.cfg...

---

### Post by MAFoElffen on 2023-05-24
Variable GRUB_OS_PROBER_SKIP_LIST only works to skip entries found by script 30_os-prober... Which I now understand, that you manually turned off via the execution bit, instead of toggling off with GRUB_OS_PROBER_DISABLE...

FYI, just to answer your question about that... It won't help you with what you are trying to do, but you asked. Find the "Path" in output from 'efibootmgr -v' looking through the output of the EFI boot entry, and find the UUID from 'blkid' for the specific EFI directory. But that is not what you are doing, so will not help you to skip over and not create those two entries.
```

mafoelffen@Mikes-B460M:~$ sudo efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0000
Boot0000* Windows Boot Manager    HD(1,GPT,e72b3745-510c-481f-95f6-f721bc03e49e,0x800,0x100000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0002* ubuntu    HD(1,GPT,e72b3745-510c-481f-95f6-f721bc03e49e,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
mafoelffen@Mikes-B460M:~$ sudo blkid | grep -e 'e72b3745-510c-481f-95f6-f721bc03e49e'
/dev/nvme4n1p1: UUID="0150-726C" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e72b3745-510c-481f-95f6-f721bc03e49e"

```
Using
```

GRUB_DISABLE_SUBMENU="true'

```
Should turn off any submenus, which the Advanced Menu is a submenu. On the default top level menu's... Hmmmm.

I don't know yet "for sure". I am thinking of spinning up a VM and check into this for myself. I am now curious. I just have to update the packages in my PPA for the system-info script and mow the lawn first... LOL.

---

### Post by watchpocket on 2023-05-25
With all the scripts in /etc/grub.d/ set as executable, I do not get the error message mentioned above when I select to boot a menu item.

I DO get the two unwanted bottom menu entries (see attached pic) of "Ubuntu" and "Advanced options for Ubuntu".  

In /etc/default/grub I have: 

GRUB_DISABLE_OS_PROBER="true"  and 

(commented-out):
#GRUB_DISABLE_RECOVERY="true"
 #GRUB_DISABLE_SUBMENU="true"

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292289&stc=1[/IMG]


(I want to keep the very bottom "UEFI Firmware settings" entry. That's in my 06_custom script.)  

If I make script 10_linux UN-executable, I get rid of the 2 unwanted menu entries, but then I get the error message.

---

### Post by oldfred on 2023-05-25
The rule is not to update grub.cfg but run sudo update-grub to create it. That uses the scripts & grub configuration settings.
But it sounds like you are the exception to the rule.

I have just installed grub to a flash drive with no install & manually created my own grub.cfg.

You can turn off all scripts & create your own grub.cfg that is just a copy of your 06_custom and maybe some of the settings from /etc/default/grub included. How does your grub.cfg differ from your 06_custom?

---

### Post by MAFoElffen on 2023-05-26
@oldfred --
That's what I was thinking about... If he generated the grub.cfg file, then edited it to remove all the unwanted menu entries...

Then set the file to read-only:
```

chmod 0444 /boot/grub/grub.cfg

```
Then it would protect it from getting 'updated' / changed. Keeping another copy of it, for the just in cases... That way it would have all the defines for gfxmode and such inside it.

Just trying to think of things. That's what we used to do before that file was dynamically written.And when resolv.conf got changed to dynamic, and needed a helper...

---

### Post by oldfred on 2023-05-26
You also can just change all the scripts to be not executable.  Not sure if then any issue when it tries to run update or not.

---

### Post by watchpocket on 2023-05-26
> **oldfred said:**
> How does your grub.cfg differ from your 06_custom?

06_custom contains: 

(a)   the menu-entry code for the first six menu (and submenu) items that are in the pic above;
(b)   the 41_custom script because I have a small custom.cfg file that provides the colors for the grub menu.

That's all that is in 06_custom.

-------------------------------------------------------

the /boot/grub/grub.cfg file contains much more:

(a)   a ### BEGIN /etc/grub.d/00_header ### section;
(b)   a ### BEGIN /etc/grub.d/05_debian_theme ### section;
(c)   a ### BEGIN /etc/grub.d/06_custom ### section (which is a copy of my entire 06_custom);
(d)   a ### BEGIN /etc/grub.d/10_linux ### section;

and below all that is this:

```
### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###
        
### BEGIN /etc/grub.d/20_linux_xen ###
        
### END /etc/grub.d/20_linux_xen ###
        
### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###
        
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'UEFI Firmware Settings' $menuentry_id_option 'uefi-firmware' {
*.......fwsetup
}       
### END /etc/grub.d/30_uefi-firmware ###
        
### BEGIN /etc/grub.d/35_fwupd ###
### END /etc/grub.d/35_fwupd ###
        
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#       
#       
### END /etc/grub.d/40_custom ###
        
### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi      
### END /etc/grub.d/41_custom ### 
 
```

---

### Post by watchpocket on 2023-05-26
> **oldfred said:**
> You also can just change all the scripts to be not executable.  Not sure if then any issue when it tries to run update or not.

Just did that with executable off for all scripts higher that 06_custom, and at the moment, that causes the same error message to appear when I select to boot the top (main) menu item (because that happens when I make the "10_linux" script unexecutable);

and it also caused the bottom menu item "UEFI Firmware Settings" to not appear, because I made the "30_uefi_firmware" script unexecutable.


Apart from getting the menu right with no error message, this page:
<[https://help.ubuntu.com/community/Grub2/CustomMenus#Removing_Default_Script_Entries](https://help.ubuntu.com/community/Grub2/CustomMenus#Removing_Default_Script_Entries)>

describes how to be able to always boot the current kernel:
> There is a potential drawback of a custom menu when the *10_linux* and/or *30_os-prober*  scripts have been disabled. A copied Linux menuentry normally contains a  specific kernel and initrd image  version number (such as 3.2.0-24) and  will not change if a new kernel is introduced.  

If the user wishes to always boot the current kernel, the *linux* and *initrd*  lines of the can take advantage of the symlinks placed in /. These  links always point to the most recent kernel. If they are referenced in  the menuentry and the symlinks exist, the menuentry will always point to  the latest kernel.
 
Replace the normal *linux* and *initrd* references, which normally contain the complete kernel version, with the following: 

[TABLE]
[TR]
[TD]linux **/vmlinuz** root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff{[/TD]
[/TR]
[TR]
[TD]initrd **/initrd.img**[/TD]
[/TR]
[/TABLE]


I believe in my case that would be: [I]
/boot/initrd.img -->
[/I]and[I] /boot/vmlinuz -->
[/I]
I think those are the symlinks he's talking about.  What I don't understand is what UUID to put there.

---

### Post by oldfred on 2023-05-26
Some examples of custom grub.
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
This is a very long mega-thread. You may want to read beginning or first page, then jump to end & work backwards for latest posts and most current info.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by watchpocket on 2023-05-27
So the original problem was that whenever I turned off executable for the */etc/grub.d/10_linux script,* I would always get the error message: [I]

**error: can't find command 'gfxmode'**[/I] whenever I selected to boot my top main grub menu entry.

And the reason I wanted the *10_linux* script turned off is that if I left it on, I got two unwanted menu items in my grub menu:* "Ubuntu" *and *"Advanced options for Ubuntu", *when I already had all the menu items I wanted in my own *06_custom* script (except for the bottom menu item *"UEFI Firmware Settings"* which is provided by the */etc/grub.d/30_uefi_firmware* script).

First I tried (and failed) to make the */boot/grub/grub.cfg* file writeable and tried to edit it (which you cannot do, because after you do a *sudo update-grub*, the *grub.cfg* file deletes all your changes and goes back to being read-only).

But in the process of trying to do that (and looking through *grub.cfg*), I noticed this bit of code -- which is actually from the 10_linux script (though it looks different there) -- and immediately recognized it as what I needed to stop the error message:
```
### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}   
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if [ ${grub_platform} != pc ]; then
      set linux_gfx_mode=keep
    elif hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
```

So I copied this block of code from *grub.cfg* and put it at the top of my *06_custom* script and presto, the error message was gone when I booted an entry.  There may well be different ways to solve the problem, but this is how i did it, and it appears to have worked. Thanks for the tips & suggestions.

---

