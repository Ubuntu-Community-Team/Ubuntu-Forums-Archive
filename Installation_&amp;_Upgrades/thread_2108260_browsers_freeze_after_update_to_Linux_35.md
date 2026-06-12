---
title: "browsers freeze after update to Linux 35"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by kwalters on 2013-01-24
I am running Ubuntu 12.04LTS 64 bit on an AMD Athlon Dual Core 4200  64 bit with 4 Gb of RAM

Ever since the routine update which gave me Linux 35 (and continuing after a further update to Linux 36, my internet browsers are giving trouble; I use both Mozilla Firefox and Google Chromium and the problem appears in both.  It does not appear if I use Windows XP on the same machine. Those facts lead me to believe that the problem lies with Ubuntu somewhere.

What happens is that whenever I have browsed through several pages on the web, the browsers suddenly freeze. They freeze so firmly that I cannot shut the machine down as I cannot select anything and the usual keyboard Killall etc cannot be accessed.  Thus I have been reduced to turning the power off and, after that, I sometimes need 3 or 4 further reboots before my wired internet connection is made.

I dont know that much about computers, but it has all the symptoms of the machine running out of RAM. The more data intensive the pages I load, the earlier it happens; and selecting anything with movies seems to make it happen even earlier.

One one occasion (and only one) I suddenly got an error message saying Firefox was about to crash and would I like to report it before it happened.  I took advantage of that, so at least someone in the Linux world knows what I was doing at the time.  All the other arisings have left my machine frozen without warning

Any ideas out there?

Thanks

Keith Walters

---

### Post by kwalters on 2013-01-24
Further to the earlier post, I just went back to Linux 32 and surfed for an hour, seeing lots of sites and lots of videos; and there were no problems in Mozilla Firefox.  The problem MUST, as I suspected, come from one of the last 2 routine updates

---

### Post by omeomi on 2013-01-24
Just to clearify: by Linux 35,36,etc. you are referring to the kernel versions (3.5, 3.6)?

Also, when the system freezes it the browser the only thing you have running? And can you still use CTRL+ALT+F1 to get to a terminal?

---

### Post by kwalters on 2013-01-24
Thanks for that response

Apologies for the sloppy language.  Yes I mean kernel numbers, but all should be prefixed by 3.0.2..  Thus the kernels I mentioned were 3.0.2.36,  3.0.2.35 and 3.0.2.32

In each case the browser (either Mozilla (normally) or Chromium (occasionally) was the only thing running.   I had not heard of ctrl-Alt-F1;  I have always used Ctrl-Alt-T to get a terminal. 

I just tried Ctrl-Alt-F1 and it gave me a terminal (but I could not find my way out again!)  However, the system was not frozen at that time.  ON previous freezes I tried every key combination I have ever heard of  - but with zero effect

Thanks

Keith Walters

---

### Post by grahammechanical on 2013-01-24
This is why earlier versions of the Linux kernel are left on the system and in the boot menu. Simply continue to boot into the last kernel image that worked for you (Linux 3.0.2.32 - yes?).

In time there will be other kernel updates and this problem gets fixed and then you can boot into the last kernel. In a few weeks 12.04 is due to get the kernel series that is used in 12.10 - Linux 3.5.0 series.

It worked fine for me when I tested this upgrade a few weeks ago. I am testing 13.04 and the kernel went from 3.5.0 series to 3.7.0 series but then further updates to the kernel broke the OS. I had to boot into the 3.7.0-0 kernel to get to a desktop until kernel 3.7.0-5 came along. Now 13.04 is using 3.8.0-1 kernel.

This is how Linux/Ubuntu is developed. Ubuntu 12.04 will be around for 5 years. It will need to be able to work with the latest hardware that comes out in those years. So, 12.04 needs to keep up with development in the Linux kernel as well as developments in other components of the distribution.

Regards.

---

### Post by kwalters on 2013-01-24
Thanks for that.  I can wait a bit.  But how will anyone know that this problem needs fixing in later kernels?

KW

---

