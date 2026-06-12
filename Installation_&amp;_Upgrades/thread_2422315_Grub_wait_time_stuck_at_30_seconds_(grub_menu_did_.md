---
title: "Grub wait time stuck at 30 seconds (grub menu did not used to appear)"
date: 2019-07-05
forum: Installation &amp; Upgrades
---

### Post by crisisengine on 2019-07-05
Hello there,

I just installed the new lts version (18.04) of Ubuntu budgie. I did a clean installation from a dvd-rw on my hp-15 laptop the only runs ubuntu (I previously had lts version 16.04 of of budgie). When using that version, the grub boot menu never appeared at startup. This was fine by me as there was only one OS on there so it didn't matter at all. Now, with this new version, the grub menu has appeared again. I can't even change the time it sticks around - stuck at 30 seconds (because my system is UEFI). Basically, I want to make the grub menu go away again (it worked before so I assume this is possible). What solutions do you have to this? Should I use a different boot manager? 

Thanks!

Joe

---

### Post by deadflowr on 2019-07-05
Look at your grub config file in /etc/default/grub.
Post it if you need help understanding it.

---

### Post by uRock on 2019-07-05
You should be able to edit grub by running the following to open the configuration file,
```
sudo -H gedit /etc/default/grub
```
I was looking at this link, [https://askubuntu.com/questions/111085/how-do-i-hide-the-grub-menu-showing-up-at-the-beginning-of-boot](https://askubuntu.com/questions/111085/how-do-i-hide-the-grub-menu-showing-up-at-the-beginning-of-boot), and found that it says to change GRUB_HIDDEN_TIMEOUT_QUIET to false, but I am not seeing that option in my 18.04 grub file. Here  is what my grub config looks like, which makes me think you'd need to change your GRUB_TIMEOUT_STYLE to "hidden".
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Once you save your changes, you'll need to run the following command to seal the deal. Restart the system and see if that worked out.
```
sudo update-grub
```

---

### Post by CatKiller on 2019-07-05
Sorry, I can't resist.

> **uRock said:**
> I was looking at this link, [https://askubuntu.com/questions/111085/how-do-i-hide-the-grub-menu-showing-up-at-the-beginning-of-boot](https://askubuntu.com/questions/111085/how-do-i-hide-the-grub-menu-showing-up-at-the-beginning-of-boot), and found that it says to change GRUB_HIDDEN_TIMEOUT_QUIET to false, but I am not seeing that option in my 18.04 grub file. 

[Grub manual](https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html):
> 
‘GRUB_HIDDEN_TIMEOUT’
Wait this many seconds before displaying the menu.  If ESC is pressed during that time, display the menu and wait for input according to ‘GRUB_TIMEOUT’.  If a hotkey associated with a menu entry is pressed, boot the associated menu entry immediately.  If the timeout expires before either of these happens, display the menu for the number of seconds specified in ‘GRUB_TIMEOUT’ before booting the default entry. 

 If you set ‘GRUB_HIDDEN_TIMEOUT’, you should also set ‘GRUB_TIMEOUT=0’ so that the menu is not displayed at all unless ESC is pressed. 

 This option is unset by default, and is deprecated in favour of the less confusing ‘GRUB_TIMEOUT_STYLE=countdown’ or ‘GRUB_TIMEOUT_STYLE=hidden’. 

‘GRUB_HIDDEN_TIMEOUT_QUIET’

    In conjunction with ‘GRUB_HIDDEN_TIMEOUT’, set this to ‘true’ to suppress the verbose countdown while waiting for a key to be pressed before displaying the menu.

    This option is unset by default, and is deprecated in favour of the less confusing ‘GRUB_TIMEOUT_STYLE=countdown’. 
 

It would probably be helpful for the OP to determine whether the Grub menu has started appearing because they still have 16.04 installed as well. The default behaviour of a new install is to hide the Grub menu unless there is another OS installed.

---

### Post by uRock on 2019-07-05
> **CatKiller said:**
> Sorry, I can't resist.



[Grub manual](https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html):


It would probably be helpful for the OP to determine whether the Grub menu has started appearing because they still have 16.04 installed as well. The default behaviour of a new install is to hide the Grub menu unless there is another OS installed.

The config I shared is the default created by the installer, if that's outdated, then "it wasn't me."  Thanks for the info, though.  Without seeing the OP's file, I can't know how his was installed, but I am sure you're correct.

---

### Post by CatKiller on 2019-07-06
> **uRock said:**
> The config I shared is the default created by the installer, if that's outdated, then "it wasn't me."  Thanks for the info, though.

No, no, I was saying that the askubuntu advice was outdated. Although I forgot to copy-and-paste the important bit; oops. 

The "can't resist" part was to passing on information even when not explicitly asked to do so.

---

### Post by uRock on 2019-07-06
> **CatKiller said:**
> No, no, I was saying that the askubuntu advice was outdated. Although I forgot to copy-and-paste the important bit; oops. 

The "can't resist" part was to passing on information even when not explicitly asked to do so.

Oh, ok. I am glad you posted what you did, though. Reminded me to check the man page, instead of thread searching. No worries.

---

### Post by jeremy31 on 2019-07-06
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/16](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1800722/comments/16)

---

### Post by Frogs Hair on 2019-07-07
16.04 would have been Budgie Remix and not an official flavor yet, so there may be differences.

---

### Post by crisisengine on 2019-07-15
Hey guys - sorry for being absent, all this looks really useful. I don't have 16.04 installed any more as the dvd-rw did a clean installation - I'm pretty sure it's been removed. So yeah, I think I know how to change the settings in the right way, I'm just unsure how to stop the system from overriding them because it's UEFI. I will try restarting now and see if CatKiller's suggested modifications work.

By the way, here's what I get when I do sudo update-grub:
Found linux image: /boot/vmlinuz-4.18.0-25-generic
Found initrd image: /boot/initrd.img-4.18.0-25-generic
Found linux image: /boot/vmlinuz-4.18.0-15-generic
Found initrd image: /boot/initrd.img-4.18.0-15-generic
Found linux image: /boot/vmlinuz-4.18.0-25-generic
Found initrd image: /boot/initrd.img-4.18.0-25-generic
Found linux image: /boot/vmlinuz-4.18.0-15-generic
Found initrd image: /boot/initrd.img-4.18.0-15-generic
Adding boot menu entry for EFI firmware configuration
done

---

