---
title: "libc.so.6: cannot open shared object file"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by juanJosepablos on 2009-12-08
Hi,
I have download the 20091208/lucid-desktop-i386.iso
The system boots up ok. 
But is not able to get and ip address from the dhcp server. so i run:

```
dhclient eth0
```

And I get a 
```
dhclient: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
```

Has anyone else got same error?

---

### Post by slakkie on 2009-12-08
[I had similar issues not too long ago.](http://ubuntuforums.org/showthread.php?t=1347444)

Could you install the debsums package and run the following command?

```

sudo aptitude install debsums
sudo debsums -c > /path/to/file.log

```

When that is done:

```

# Find out the amount of missing files
grep  -c "missing" /path/to/file.log

# Find out which packages are missing files:
grep  "missing" debsums-c.log | awk '{NF=NF-1} {print $NF}' | sort -u

# Count the amount of packages missing files:
grep  "missing" debsums-c.log | awk '{NF=NF-1} {print $NF}' | sort -u | wc -l 

```

What you can then do is:
```

sudo aptitude reinstall $(grep  "missing" debsums-c.log | awk '{NF=NF-1} {print $NF}' | sort -u)

```

And to fix possible checksum errors, do the following:

```

pkg=$(debsums -l)
[ -n "$pkg" ] && sudo aptitude --download-only reinstall $pkg
sudo debsums --generate=keep,nocheck /var/cache/apt/archives/*.deb

```

---

### Post by juanJosepablos on 2009-12-08
the Trouble is that I am usin the live cd. I am testing with the alternate iso right now. And at the moment the only problem seem to be that 'cdrom-detect/try-usb=true' is not enable if I copy from iso to usb

---

### Post by juanJosepablos on 2009-12-08
ok. I managed to boot up. daily/20091208/ and install the system, but when it starts a blank screen show up and I am not able to changes consolo or any meaing to find out what is the problem.

 Any pointers for debugging this problem?

The systems is an old ACER 1410 with 512Mb and 60Gb Hd. I have been using ubuntu in this laptop for a few years, It was working fine with 8.04. Please advice.

---

### Post by slakkie on 2009-12-08
> **juanJosepablos said:**
> the Trouble is that I am usin the live cd. I am testing with the alternate iso right now. And at the moment the only problem seem to be that 'cdrom-detect/try-usb=true' is not enable if I copy from iso to usb

That shouldn't be an issue. Just don't reboot (which is not required to make it work).

---

### Post by juanJosepablos on 2009-12-08
ok, even if the network interface is not working, I will try to add them using other usb. Is this test going to help anyone here?

I can wait for the next live cd to popup, but if this test helps to eliminate another bug, I will exec those commands.

---

### Post by juanJosepablos on 2009-12-09
I am testing alpha1 right now, this problem is not longer valid.

---

