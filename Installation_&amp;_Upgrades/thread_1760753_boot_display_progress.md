---
title: "boot display progress?"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by DaleEMoore on 2011-05-17
I have a several second blank screen between my GRUB2 menu and the login screen. Ubuntu versions prior to 11.04 would show me what's going on instead of only showing a blank screen. Can I change my /etc/default/grub which is currently```
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
``` then run update-grub to see the text of what's happening between the GRUB2 menu and the login screen?

---

### Post by DaleEMoore on 2011-05-23
nudge

---

### Post by linuxinstalledfromhdd on 2011-05-23
It should be:

GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

---

### Post by DaleEMoore on 2011-05-23
> **linuxinstalledfromhdd said:**
> It should be:

GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

I appreciate your attempt to help, and I'll be trying your suggestion in a few minutes; but, did you realize the definition of GRUB_TIMEOUT per the [manpage]("http://www.gnu.org/software/grub/manual/grub.html") is:[INDENT]‘GRUB_TIMEOUT’
Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is ‘5’. Set to ‘0’ to boot immediately without displaying the menu, or to ‘-1’ to wait indefinitely.
[/INDENT]

But, hey; I might be wrong assuming GRUB_TIMEOUT will not effect the detail boot display and will give her a try.

---

### Post by DaleEMoore on 2011-05-23
Dear linuxinstalledfromhdd;

Your suggestion to make GRUB_TIMEOUT=10 instead of the GRUB_TIMEOUT=3 I had made no difference to the display after the timeout completed. Perhaps I did not make myself clear to you that after the 3 (or 10) second timeout the screen goes blank until the login screen appears. Prior to Ubuntu 11.04 the boot details displayed. Now that I have Ubuntu 11.04 installed on lots and lots of computers; none of them show me the boot detail display.

Please don't let this little set back stop you; the answer might be right around the corner... do you have any other suggestions?

I look forward to hearing from you,
Dale E. Moore

---

### Post by linuxinstalledfromhdd on 2011-05-23
I was helping someone else. Sorry about that.  My instinct was correct about that. It's not the timeout at all. It's something completely different and unrelated with that.  Does this happen with the LIVE USB stick of Ubuntu as well?

---

### Post by DaleEMoore on 2011-05-23
> **linuxinstalledfromhdd said:**
> Does this happen with the LIVE USB stick of Ubuntu as well?

It happens with every 11.04 I've tried, LIVE CD, HD installed, tweeked GRUB; though I've never specifically tried a LIVE USB stick.

---

### Post by DaleEMoore on 2011-05-25
nudge

---

### Post by DaleEMoore on 2011-05-30
wink

---

### Post by CVGH on 2011-05-31
Get rid of "quiet splash", save and run sudo update-grub


```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

```I think that is what you are after...

---

### Post by DaleEMoore on 2011-05-31
> **CVGH said:**
> Get rid of "quiet splash", save and run sudo update-grub


```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

```I think that is what you are after...

Hi CVGH;

My /etc/default/grub (that's what you are suggesting I change, right?) only contains```
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```and I ran update-grub after setting it that-a-way. Does that meet your suggestion?

Not having GRUB_CMDLINE_LINUX_DEFAULT="quite splash" did not improve the situation.

I look forward to hearing from you,
Dale E. Moore

---

### Post by CVGH on 2011-06-01
Hi Dale,

Seems like your grub is missing some stuff..
I would make a copy of yours then try this as grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=" splash vga=789"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

This is from 10.10, but should be ok..

Brian

---

### Post by DaleEMoore on 2011-06-01
> **CVGH said:**
> try this as /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=" splash vga=789"
```This is from 10.10, but should be ok..

Brian

It helped not at all Brian. You might try it in 11.04 and notice that nothing seems to provide the detail display. But, thanks; I really appreciate you trying this for me!

---

### Post by DaleEMoore on 2011-09-12
I went to openSUSE 11.4 and didn't encounter this problem.

I've come back to Ubuntu 11.10 beta 1 and there is more detail when booting, thanks to the powers that be!

---

