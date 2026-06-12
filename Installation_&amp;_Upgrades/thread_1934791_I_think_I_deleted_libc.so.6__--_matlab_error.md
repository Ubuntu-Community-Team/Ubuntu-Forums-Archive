---
title: "I think I deleted libc.so.6  -- matlab error"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by lifemath on 2012-03-02
Hi, all.

I'm trying to get matlab to work on my ubuntu 11.10 installed on a partition on a mac (snow leopard). I installed ubuntu 11.10 but when I installed and started matlab, it gave me this libc.so.6 error not found.

I tried

$locate libc.so.6

then, it gives me only one location unlike I've read in other sites. 

/lib/i386-linux-gnu/libc.so.6

I think I used a rm command following this and that instruction in a haste. 

Is there a solution for this?

I tried the sudo -ln command for 32 bit but it says creating something and file exists message. I don't know what it means.

Please help!

---

### Post by MAFoElffen on 2012-03-03
```

sudo apt-get install lib6 lib6-i686 ppu-sysroot

```
With lib6 > /lib/libc.so.6
With lib6-i686 > /lib/tls/i686/cmov/libc.so.6
With ppu-sysroot > /usr/lib/cell/sysroot/lib/libc.so.6

Is that the info you were looking for?  You could go into synaptic and see if they are installed and reinstall package(s) that is.

---

### Post by matt_symes on 2012-03-03
Hi

> I think I deleted libc.so.6

I have done that before :P I could not run any commands requiring libc so next to nothing in the terminal would run.

As i'm sure you know, it's actually a symlink to the correct library.

On my 64bit system with the 32 bit libs installed.

```
matthew@matthew-Aspire-7540:~$ ls -l /lib/i386-linux-gnu/libc.so.6 /lib/x86_64-linux-gnu/libc.so.6
lrwxrwxrwx 1 root root 12 Feb 24 06:43 /lib/i386-linux-gnu/libc.so.6 -> libc-2.15.so
lrwxrwxrwx 1 root root 12 Feb 24 00:03 /lib/x86_64-linux-gnu/libc.so.6 -> libc-2.15.so
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ readlink -f /lib/i386-linux-gnu/libc.so.6
/lib/i386-linux-gnu/libc-2.15.so
matthew@matthew-Aspire-7540:~$ 
```

Your library version my be different as i am currently in Precise (12.04)

I used a LiveUSB to recreate the links.

Kind regards

---

### Post by lifemath on 2012-03-03
Hi, guys!

Thank you for your suggestions. I tried this and that and when I used 'locate libc.so.t' command, it showed that I did have the file. But somehow, matlab was not locating to use it. And I also used the symlink commands many people recommended here and there but it was not working. I finally tried it as a root user but it still didn't work.

Later, I went into the ubuntu software center and checked if I had c in stalled. I did have c installed but there were some add-ons still left. I clicked all the add-ons and installed them. And interestingly, the link command suddenly worked. And I don't get the error message anymore. 

I'm a complete newbie for everything: to ubuntu, matlab, etc. So, I don't know how it exactly worked. But it worked!

---

