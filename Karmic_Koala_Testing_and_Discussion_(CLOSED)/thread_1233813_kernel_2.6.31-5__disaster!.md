---
title: "kernel 2.6.31-5:  disaster!"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-08-07
i have many problems with latest kernel:

- gdm freeze
- using tty, when i use sudo/su, i can't have privilege and system freeze
- my eth0 doesn't work ( atheros AR8121)

---

### Post by taavikko on 2009-08-07
Wow, that's a full blown report and diagnostics of problems ;)

check the "dmesg" logs for any clues, and any logs for that matter.
There might also be "kernel.crash" in /var/crash/ folder, use it to report if needed.

---

### Post by gnomeuser on 2009-08-07
ubuntu-bug -p linux a should collect the right information and file a bugreport for you.

---

### Post by philinux on 2009-08-07
> **gnomeuser said:**
> ubuntu-bug -p linux a should collect the right information and file a bugreport for you.

Hi,

Just checked man pages and -p switch is not listed. Whats it do and are there any others not listed.

---

### Post by biasquez on 2009-08-07
> **gnomeuser said:**
> ubuntu-bug -p linux a should collect the right information and file a bugreport for you.

i can't do login and i can't use eth0 to upload bugreport...

---

### Post by diebels on 2009-08-07
Can you log in with the previous kernel?

---

### Post by jerrylamos on 2009-08-07
> **gnomeuser said:**
> ubuntu-bug -p linux a should collect the right information and file a bugreport for you.

ubuntu-bug in my experience does not work unless you have a gdm working.

If the problem is the gdm doesn't work, then ubuntu-bug won't either.

ubuntu-bug tries to run but then presents a menu about saving the report however ubuntu-bug is hard coded to expect a gdm to be running and will not accept any input to save the report.  ubuntu-bug does not have a default to save the report.

If the gdm was running wouldn't need ubuntu-bug to report it.

Jerry

---

### Post by gnomeuser on 2009-08-07
> **jerrylamos said:**
> ubuntu-bug in my experience does not work unless you have a gdm working.

If the problem is the gdm doesn't work, then ubuntu-bug won't either.

ubuntu-bug tries to run but then presents a menu about saving the report however ubuntu-bug is hard coded to expect a gdm to be running and will not accept any input to save the report.  ubuntu-bug does not have a default to save the report.

If the gdm was running wouldn't need ubuntu-bug to report it.

Jerry

if I remember correctly though it can collect a report for you file, then boot into the machine in the old kernel and submit. I could be mistaken though. Regardless we need a way to get a proper bugreport and some more information.

---

### Post by xebian on 2009-08-07
I think it's the apparmor causing your problem.  Boot to recovery and then get rid/purge apparmor and then reboot.

---

### Post by rajeev1204 on 2009-08-07
Iam getting an error every second time saying ... waiting for state of solid state devices. then it hangs.

---

### Post by biasquez on 2009-08-07
problems fixed! ( i have a kernel panic when kernel load dvb_usb_af9015 firmware ). but now, wifi (iwlagn-5000) and eth0 (module atl1e) doesn't work :(

---

### Post by caryb on 2009-08-07
With the exception of no wireless mine is working flawlessly on 31-5 (64bit) kernel


Cary

---

