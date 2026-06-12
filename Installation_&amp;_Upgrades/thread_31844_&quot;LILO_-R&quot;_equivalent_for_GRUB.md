---
title: "&quot;LILO -R&quot; equivalent for GRUB"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by rms46 on 2005-05-05
Hi

Is there anyway to tell GRUB to boot a certain mode ONCE after "shutdown -r" (like lilo -R label)? That would be very handy for testing a remote system (with no direct access).

Thank you!

---

### Post by rms46 on 2005-05-05
May I conclude:
[list]
[*]This was the wrong forum to ask?
[*]This question was too difficult to be answered
[*]I should wait a little bit longer
[*]other:
[/list]

---

### Post by nad on 2005-05-05
No. There is no similar command for grub, however, it would be trivial to write a self-removing or conditional script, placed with your init scripts, that would either modify or replace the grub config for the following boot.

Grub can be conrolled through the serial port. Whether tcp support is being considered for grub2, I don't know. You may wish to peruse development at [www.gnu.org](www.gnu.org) .

---

### Post by rms46 on 2005-05-05
Apology: I am new to GRUB. At this stage, the script is  no "trivial" for me.
(I am refering to [http://www.gnu.org/software/grub/manual/grub.html#Commands](http://www.gnu.org/software/grub/manual/grub.html#Commands) )

Basically, I would like to "TEST" a configuration at a remote site. With lilo, I would invoke: 
> # lilo -R TheNewLabel
# reboot

**[If nothing happen, I would call the remote "operator on duty" to "hard reset" my computer]**

May I know how to do that with a script of GRUB?

thank you!

---

### Post by nad on 2005-05-06
My suggestion will work only if the operating system boots through the special init script.

If you suspect that your test configuration will cause grub to hang, simply use the fallback option to indicate a good default. Once control is passed to the init image, only a hard reset and repair will cure a hung kernel load. In this case, use lilo or keep the operators supplied with pizza, beer and instructions.

---

### Post by Elendur on 2005-05-15
I think the simplest thing you can do is have two versions of /boot/grub/menu.lst : one which loads the safe kernel by default (you can name it menu.lst.safe), and one which loads the new kernel by default (menu.lst). Then you add a startup script, or at/cron job or whatever to copy menu.lst.safe to menu.lst.

---

### Post by rms46 on 2005-05-16
[QUOTE=Elendur]I think the simplest thing you can do is have two versions of /boot/grub/menu.lst :[/QUOTE]

Unfortunately, this way will not solve the "remote test problem". I guess, that using lilo will be more appropriate for this purpose.

1. Normal Usage: GRUB
2. When "testing a remote systems"; use LILO; 
3. If it works; switch to GRUB again
4. If it does not; "ask the operator on duty to reset the computer" (in LILO mode); then switch to GRUB.

regards,

---

### Post by nad on 2005-05-16
There is also a 'panic=' boot option.

From tldp.org:

The `panic=' Argument

In the unlikely event of a kernel panic (i.e. an internal error that has been detected by the kernel, and which the kernel decides is serious enough to moan loudly and then halt everything), the default behaviour is to just sit there until someone comes along and notices the panic message on the screen and reboots the machine. However if a machine is running unattended in an isolated location it may be desirable for it to automatically reset itself so that the machine comes back on line. For example, using panic=30 at boot would cause the kernel to try and reboot itself 30 seconds after the kernel panic happened. A value of zero gives the default behaviour, which is to wait forever.

Note that this timeout value can also be read and set via the /proc/sys/kernel/panic sysctl interface.

end paste.

You might be able to use this in conjuction with a known good configuration.

---

