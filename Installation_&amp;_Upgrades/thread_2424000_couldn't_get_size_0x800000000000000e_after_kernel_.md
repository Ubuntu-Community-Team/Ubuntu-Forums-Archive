---
title: "couldn't get size 0x800000000000000e after kernel upgrade"
date: 2019-08-01
forum: Installation &amp; Upgrades
---

### Post by panja on 2019-08-01
I ran "apt update && apt upgrade".
My kernel got updated to GNU/Linux 5.0.0-23-generic x86_64 and now when booting I'm having an error message:
[    1.494511] Couldn't get size 0x800000000000000e

Intel NUC7i5BNK  (latest bios: BNKBL357.86A.0080) with Ubuntu Server 18.04.2 LTS with Secure Boot disabled.

Any one know how to fix this?

---

### Post by panja on 2019-08-02
Any one?

---

### Post by &amp;wP*!) on 2019-08-02
Have you tried with the enabled Secure Boot?

---

### Post by panja on 2019-08-02
Yes, I've tried it with Secure Boot enabled.
This gives me the same problem unfortunately.

---

### Post by Dennis N on 2019-08-02
> [ 1.494511] Couldn't get size 0x800000000000000e
Does your system still boot?

---

### Post by panja on 2019-08-02
It boots and I can use it without problems.
It's just not really nice to see error messages.

I'm using this machine in the living room as a retro game machine.
Normally it boots up without any prompts or screens but now I have this error message.

It's just not right...

---

### Post by Dennis N on 2019-08-02
I've seen the same 'couldn't get size' message several times on some computers in the past (but admittedly not for a long while, though). As long as there is no noticable effect on operation, you should consider it 'informational' and just live with it it. With some future update, it will probably go away.

You probably know this, but if you run **journalctl -b** you will see the journal messages generated on startup for the most recent boot. Lots of similar scary chatter in there, some even labeled with ERROR and WARNING. Sometimes some push through the splash barrier.

I just ran that on this computer looking for 'error' in the output:
```

[dmn@sydney ~]$ journalctl -b | grep -i error
Aug 02 06:26:45 sydney kernel: RAS: Correctable Errors collector initialized.
Aug 02 06:26:45 sydney kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT4._GTF.DSSP], AE_NOT_FOUND (20190509/psargs-330)
Aug 02 06:26:45 sydney kernel: ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20190509/psparse-529)
Aug 02 06:26:45 sydney kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT4._GTF.DSSP], AE_NOT_FOUND (20190509/psargs-330)
Aug 02 06:26:45 sydney kernel: ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20190509/psparse-529)
Aug 02 06:26:46 sydney snapd[569]: stateengine.go:108: state ensure error: Get https://api.snapcraft.io/api/v1/snaps/sections: dial tcp: lookup api.snapcraft.io: no such host
Aug 02 06:26:54 sydney lightdm[598]: Error opening audit socket: Protocol not supported
Aug 02 06:27:20 sydney pulseaudio[903]: E: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply.

---and there is more----
```

None of this appeared on the screen on startup. Scary, but don't be too alarmed.

---

### Post by oldos2er on 2019-08-02
>  journalctrl -b

Should be journalctl -b

---

### Post by Dennis N on 2019-08-02
> Should be journalctl -b
Thanks; and corrected.

---

### Post by panja on 2019-08-02
Thanks guys!

I do know it’s more an informational message than anything else and normally I won’t be bothered much. But it’s a living room machine which is used by daughters and wife as well. They do get scared with messages like this. &#128514;

---

### Post by VMC on 2019-08-02
output ```
efibootmgr
```
When you updated do you know if your grub.cfg was also changed?

I fix mine a different way. But I see this message when I install ubuntu but is controlled by another os.

---

### Post by panja on 2019-08-07
Sorry for the late reply...


Output efibootmgr:

BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0000,0001
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0003* ubuntu


Last time the file was modified:
```
-r--r--r-- 1 root root    7889 Aug  1 19:56 grub.cfg
```

---

### Post by &amp;wP*!) on 2019-08-07
This error exists for a long time in the Linux kernel of many distros. According to the link [https://bugzilla.redhat.com/show_bug.cgi?id=974841](https://bugzilla.redhat.com/show_bug.cgi?id=974841) , it can be safely ignored if you don't use SecureBoot related stuff.

---

