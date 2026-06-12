---
title: "How to boot in recovery mode"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by arun-3 on 2014-09-23
I tried to login through recovery mode .Login Screen appears after typing the password nothing appears.
Can anyone please tell how to get system recover in recovery mode in the root shell script option or any other option available through live cd like that. Since, i have important data on that system.


Thanks in advance,

Best Regards,

Arun

---

### Post by Bashing-om on 2014-09-23
arun-3; Hi !

Did the installation of the SIS graphics driver ( from another thread ) break the display ?
In any event, to get to a terminal try this:
At the grub boot menu press the 'e' key for edit -> boot parameter screen; arrow down and across to the terms "quiet splash" and replace them with the term "text", key combo ctl+x to continue the boot process to a text terminal (TTY1). Log on here with username and pass word - no response to the screen when password is entered). OK, IF you now have access to the system, what now do you want to do ?

[INDENT][INDENT]in process of help
[/INDENT][/INDENT]

---

### Post by arun-3 on 2014-09-24
hi i tried by changing quiet splash to text and press ctrl+x after that tty login appears but its not accepting user name and password says login credtional fails. Please suggest me a idea to resolve this.

---

### Post by Bashing-om on 2014-09-24
arun-3; Hummm ....

This is indeed getting deeper. Let's try this to gain access to the system.
Boot to grub's boot menu -> advanced options -> choose a "recovery" kernel -> root access.
The access granted at this level will suffice for the current need to know.
What returns now from the terminal commands:
```

ls -al ~/.Xauthority
ls -al ~/.ICEauthority
ls -al /home
egrep ':[0-9]{4}:' /etc/passwd

``` to explore the possibility that we will have to delve into the 'sudoers' file to regain authorizations.

[INDENT][INDENT]look'n to find the why
[/INDENT][/INDENT]

---

### Post by arun-3 on 2014-09-29
Thanks, Bashing-om . i will try this code and let you know.

---

### Post by nerdtron on 2014-09-29
> **arun-3 said:**
> I tried to login through recovery mode .Login Screen appears after typing the password nothing appears.
Can anyone please tell how to get system recover in recovery mode in the root shell script option or any other option available through live cd like that. Since, i have important data on that system.


Thanks in advance,

Best Regards,

Arun

It seems like a display issue like Bashing-om said.

Anyway as a last resort, you can create a bootable USB drive with ubuntu on it. Boot on it. then you can browse your files in the system. You can even edit some config files while in Live Mode.

---

