---
title: "Adding a menu entry to grub2"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-08-28
I have both Ubuntu 9.10 and Sabayon 4.2 installed on my laptop. Sabayon (along with it's boot loader) resides on sda8 on my hard drive. Ubuntu 9.10 resides on sda6, and grub2 resides on sda1 (Which is mounted as Ubuntu 9.10 /boot directory)

I am trying to add an entry for Sabayon to my grub so I can choose to boot into it when I want to... I ran the grub auto updated and it looked like it had worked... ```
jeff@sager-lintop:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found memtest86+ image: /memtest86+.bin
Found Gentoo Base System release 2.0.0 on /dev/sda8
done

```

How ever when I reboot I did not have a new menu entry in my grub entires... So I did some reading [here](https://wiki.ubuntu.com/Grub2) and create a custom.sh (and made it executable) in my /etc/grub.d/ directory. The contents of my custom.sh are: ```
echo "Adding Sabayon Linux to the Menu..."
cat << EOF
menuentry "Sabayon Linux - 4.2" {
        set root=(hd0,7)
        linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=c1cd8123-e519-43bf-b3eb-451423824159 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda2 real_resume=swap:/dev/sda2
        initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
EOF
``` I ran the update-grub2 command again and get the same results as before (for some reason it failed to show my echo command) - but anywho upon investigating my /boot/grub/grub.cfg it had indeed added the entry for Sabayon this time.

Only once I reboot threw me an error message "you need to load the kernel first" when I selected my Sabayon option. I know I must be missing something but I cannot quiet figure it out... any suggestions?

Thanks,
~Jeff

PS: This is my menu.lst from Sabayon to show that I have the kernels and such right in my custom.sh: ```
title Sabayon Linux (kernel-genkernel-x86_64-2.6.29-sabayon)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=c1cd8123-e519-43bf-b3eb-451423824159 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda2 real_resume=swap:/dev/sda2
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault
```

---

### Post by VMC on 2009-08-28
"...Sabayon (along with it's boot loader) resides on sda8..."

Change ```
"set root=(hd0,7)" to "set root=(hd0,8)"
```

---

### Post by beastrace91 on 2009-08-28
Haha. That solved the issue. At least I under stand how grub2 works a little bit better even if I am *slightly* retarded.

~Jeff

---

### Post by ranch hand on 2009-08-28
GREAT.

Grub2 is, I think, going to rock.  It is a little rough when it comes to picking wierd OS' up.  I had the same problem with my Mandriva installations.

Good work.  Pat ourself on the back.

---

### Post by VMC on 2009-08-28
> **ranch hand said:**
> GREAT.

Grub2 is, I think, going to rock.  It is a little rough when it comes to picking wierd OS' up.  I had the same problem with my Mandriva installations.

Good work.  Pat ourself on the back.

I mentioned that it misses Fedora's initrd completely. I wonder if I should file a bug of is there some script that I missed.

---

### Post by ranch hand on 2009-08-28
> **VMC said:**
> I mentioned that it misses Fedora's initrd completely. I wonder if I should file a bug of is there some script that I missed.
```

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```
This in the entry for one of my Mandriva OS'.

I believe that if you use it as a pattern it will work for about anything.

You may need to add "set root=(hd0,12)" above "linux (hd0,12)/boot/vmlinuz" to make it work although I, obviously, didn't.

Remember that grub2 numbers the drive the same as grub-legacy but the partition like gparted.

---

### Post by VMC on 2009-08-28
Here's part of the script in "10" that I think it suppose to detect "initrd", but it misses Fedora:

...
```
initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi
```

---

### Post by beastrace91 on 2009-08-29
The really strange thing is that it detected my Sabayon install - ```
Found Gentoo Base System release 2.0.0 on /dev/sda8

```

But it just did not create an entry for it...

~Jeff

---

