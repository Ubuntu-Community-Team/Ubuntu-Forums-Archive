---
title: "Grub boot menu resets to default after installing updates"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by fireman biff on 2008-02-22
Sometimes after updates my /boot/grub/menu.lst gets reset to the default version and I have to manually set it back to the way I want it. Is there any way to prevent this from happening?

---

### Post by Pumalite on 2008-02-22
Edit menu.lst and set kopt and groot permanently.

---

### Post by fireman biff on 2008-02-23
> **Pumalite said:**
> Edit menu.lst and set kopt and groot permanently.

The section of the file relating to kopt and groot is as follows:

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e48942aa-9fb1-4fed-9a82-7433cc3b0426 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```

What exactly am I supposed to to with it?

---

### Post by Pumalite on 2008-02-23
Leave 'kopt' as it is and uncomment (remove #) 'groot'

---

### Post by dstew on 2008-02-23
If your grub root device is (hd1,0) then edit # groot:```
# groot=(hd1,0)
```Do not remove the # from in front of the line. Grub uses this value to update the root arguments in the menu items whenever update-grub is run, which happens with a kernel update. See the [update-grub man page]("http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz").

---

### Post by fireman biff on 2008-02-23
> **dstew said:**
> If your grub root device is (hd1,0) then edit # groot:```
# groot=(hd1,0)
```Do not remove the # from in front of the line. Grub uses this value to update the root arguments in the menu items whenever update-grub is run, which happens with a kernel update. See the [update-grub man page]("http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz").

Thanks, I changed it to (hd0,1) which is where Ubuntu is, so part of my problem is solved.

The other part is that when update-grub runs it changes the name the entries for Ubuntu. All I really want is for the menu to show three options: Ubuntu, Debian, Windows XP. But when the file is updated I get four options:
[LIST]
[*]Ubuntu 7.10, kernel 2.6.22-14-generic
[*]Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
[*]Debian
[*]Windows XP
[/LIST]

I figured out how to get rid of the memtest, but not the recovery mode. And how do I get it to keep showing just "Ubuntu"?

---

### Post by Pumalite on 2008-02-23
Comment out the rest in menu.lst.

---

### Post by fireman biff on 2008-02-23
> **Pumalite said:**
> Comment out the rest in menu.lst.

Sorry, I wasn't clear enough. I want it to show just "Ubuntu" instead of "Ubuntu 7.10, kernel 2.6.22-14-generic" and I don't want it to show "Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)" at all. If I just comment off the recovery mode entry it gets uncommented when update-grub is run.

In other words, my boot menu should look like this, and always look like this:
[LIST]
[*]Ubuntu
[*]Debian
[*]Windows XP
[/LIST]

---

### Post by Pumalite on 2008-02-23
Bad idea. Is much better to know what kernel you are booting.

---

### Post by uidb4056 on 2008-02-23
I agree also is better not change the name but if you want you have to change in menu.lst the text right to title line with the text that you want.

---

### Post by fireman biff on 2008-02-23
> **uidb4056 said:**
> I agree also is better not change the name but if you want you have to change in menu.lst the text right to title line with the text that you want.

I know I can do that, but whenever update-grub runs it puts it back to the default. Is there a way to at least make it say "Ubuntu (2.6.22-14)" instead of "Ubuntu 7.10, kernel 2.6.22-14-generic" and keep it that way even after update-grub runs?

Also I still don't know how to get rid of the recovery mode entry and keep it removed.

---

### Post by Pumalite on 2008-02-23
Bad idea again. 'Recovery Mode' is there for a purpose; when you have a problem with your OS, well, it helps you to recover.

---

### Post by fireman biff on 2008-02-23
> **Pumalite said:**
> Bad idea again. 'Recovery Mode' is there for a purpose; when you have a problem with your OS, well, it helps you to recover.

Is there any advantage to leaving this if I have a live cd that I can use if there's a problem?

---

### Post by lha on 2008-02-23
> **fireman biff said:**
> I know I can do that, but whenever update-grub runs it puts it back to the default. Is there a way to at least make it say "Ubuntu (2.6.22-14)" instead of "Ubuntu 7.10, kernel 2.6.22-14-generic" and keep it that way even after update-grub runs?

Also I still don't know how to get rid of the recovery mode entry and keep it removed.

Substitute 'alternative=false' for 'alternative=true' in menu.lst to get rid of the recovery mode boot options.

If you want to make grub show simply "Ubuntu" instead of "Ubuntu, kernel x", you'll need to do some tinkering. Each time a new kernel is installed, a script, update-grub, is executed. Update-grub creates new menu.lst file based on the settings in the old menu.lst. You can edit update-grub so that it creates grub menu entries that suit you. Based on a quick look at update-grub, replacing lines
```
	echo -n "title		$title, " >> $buffer
	# memtest86 is not strictly a kernel
	if ! echo "$kernel_version" | grep -q ^memtest86; then
		echo -n "kernel " >> $buffer
	fi
	echo -n "$kernel_version" >> $buffer
```
in write_kernel_entry -function with
```
	echo -n "title		$title" >> $buffer
```
might get update-grub to do what you want. *N.B.* I haven't tested this; if it breaks your box, don't blame me.

Alternatively, you could use two different config files for grub: one containing a simple Ubuntu/Debian/Windows -menu that you would manage manually, and one managed by update-grub. This setup can be achieved by editing update-grub or re-installing grub so that grub reads its config from some other file instead of /boot/grub/menu.lst.

---

### Post by fireman biff on 2008-02-23
Thanks a lot, I managed to get rid of all the Ubuntu entries except the one I want.

I tried your suggestion for editing /usr/sbin/update-grub and it worked, so now I'm playing around with it to see if I can get it to say "Ubuntu (2.6.22-14)".

I have changed the line:

```
title=$(lsb_release --short --description 2>/dev/null) || title="Ubuntu"
```

to:

```
title="Ubuntu"
```

I also changed:

```

echo -n ", " >> $buffer
# memtest86 is not strictly a kernel
if ! echo "$kernel_version" | grep -q ^memtest86; then
	echo -n "kernel " >> $buffer
fi
echo -n "$kernel_version" >> $buffer
```

to:

```

echo -n " (" >> $buffer
# memtest86 is not strictly a kernel
#if ! echo "$kernel_version" | grep -q ^memtest86; then
#	echo -n "kernel " >> $buffer
#fi
echo -n "$kernel_version" >> $buffer
echo -n ")" >> $buffer
```

Those changes resulted in me getting "Ubuntu (2.6.22-14-generic)" in the menu, which I can live with. Its nicer than having the whole long string, and I can still see my kernel version. Maybe someday I'll figure out how to get rid of the "-generic" too.

I'm gonna cross my fingers and reboot my machine. Hopefully I haven't screwed myself :D

---

### Post by fireman biff on 2008-02-23
To anybody who is considering doing the same thing I did... it worked like a charm for me :)

---

### Post by lha on 2008-02-23
> **fireman biff said:**
> I'm gonna cross my fingers and reboot my machine. Hopefully I haven't screwed myself :D

BTW, if a new version of grub (as a package, through apt-get or synaptic) is installed, update-grub gets overwritten by a new version. You can prevent this from happening by using dpkg-divert to tell grub (as a package) to install the file update-grub to some other place than /sbin/update-grub.

---

