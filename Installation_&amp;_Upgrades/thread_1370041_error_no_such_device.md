---
title: "error: no such device"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by WaltherC on 2010-01-01
I was instructed to restart after installation. After booting
it shows 

[B]error: no such device: 0741bc23-b3df-4580-8595-0f55d61c0182
Press any key to continue..._[/B]

I pressed ESC and ended up at GNU GRUB version1.97~beta94
I tried booting from both OS choices 
[B]
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)[/B]

and did both memory tests with no errors. I also when back to check my disk and there is no error with the ISO file. Lastly I tried to reinstall again and the same problem occurs. 

What to I do to use Ubuntu OS?

---

### Post by drs305 on 2010-01-01
So you get to the Grub 2 menu and can run the memtests but neither the normal or recovery options?

From the grub 2 menu, try highlighting the top entry, press "e", then remove the entire line that contains "search" and the UUID. Then press CTRL-X to boot and see if it boots.

There was a bug a while ago concerning this - it's possible your install still contains it.

If you still can't boot, perhaps this will help:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")  It refers to booting from the command line. There is also a section on reinstalling Grub 2.

Let us know what happens.

---

### Post by WaltherC on 2010-01-02
Thank you, *_removing the entire line that contains "search" and the UUID_* helps. However I have to do this everytime even after I install the updates to **Ubuntu, Linux 2.6.31-16-generic**. Is there any way I could permanently remove it?

---

### Post by drs305 on 2010-01-02
> **WaltherC said:**
> Thank you, *_removing the entire line that contains "search" and the UUID_* helps. However I have to do this everytime even after I install the updates to **Ubuntu, Linux 2.6.31-16-generic**. Is there any way I could permanently remove it?

You can alter the script that generates the search line.

Open this file after making a backup:
```

sudo cp /usr/lib/grub/grub-mkconfig_lib /usr/lib/grub/grub-mkconfig_lib.bak
gksudo gedit /usr/lib/grub/grub-mkconfig_lib

```

Change:> 
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root=`${grub_probe} --device ${device} --target=drive`"
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  fi


To:
Change:> 
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  [COLOR="Red"]#[/COLOR] echo "set root=`${grub_probe} --device ${device} --target=drive`"
  [COLOR="Red"]#[/COLOR] if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
  [COLOR="Red"]#[/COLOR]  echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  [COLOR="Red"]#[/COLOR] fi


Save the file, then "sudo update-grub".

This will remove the search line from /boot/grub/grub.cfg and should solve your problem. If the *grub-pc* package is updated you may need to redo this with the new file.

---

