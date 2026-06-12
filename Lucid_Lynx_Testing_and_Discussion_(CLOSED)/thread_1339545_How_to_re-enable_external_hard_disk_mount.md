---
title: "How to re-enable external hard disk mount?"
date: 2009-11-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-11-27
Currently if I plug the external hard disk I see an error message:
```
Unable to mount DISK
Not Authorized
```

Can any of you tell me how can I solve this issue?

---

### Post by cariboo on 2009-11-27
What does dmesg say?

---

### Post by chrisccoulson on 2009-11-27
You should only see this if your session is not on the active console. What is the output of

```
ck-list-sessions
```

...from the session that you're experiencing this problem from?

---

### Post by yelo3 on 2009-11-28
Dmesg
```
[  556.512715] usb 2-3: new high speed USB device using ehci_hcd and address 3
[  556.666864] usb 2-3: configuration #1 chosen from 1 choice
[  556.719579] Initializing USB Mass Storage driver...
[  556.719775] usbcore: registered new interface driver usb-storage
[  556.720779] USB Mass Storage support registered.
[  556.725567] scsi6 : SCSI emulation for USB Mass Storage devices
[  556.725688] usb-storage: device found at 3
[  556.725690] usb-storage: waiting for device to settle before scanning
[  556.725697] usbcore: registered new interface driver ums-cypress
[  561.720533] usb-storage: device scan complete
[  561.722639] scsi 6:0:0:0: Direct-Access     WDC WD16 00BEVE-11UYT0    0000 PQ: 0 ANSI: 0
[  561.724286] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  561.728225] sd 6:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[  561.729206] sd 6:0:0:0: [sdb] Write Protect is off
[  561.729214] sd 6:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  561.729220] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  561.732055] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  561.732067]  sdb: sdb1
[  561.788128] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  561.788139] sd 6:0:0:0: [sdb] Attached SCSI disk
[  561.863304] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.863319] Descriptor sense data with sense descriptors (in hex):
[  561.863325]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  561.863347]         00 00 00 00 e0 50 
[  561.863358] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  561.885069] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.885084] Descriptor sense data with sense descriptors (in hex):
[  561.885089]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 fe 00 00 
[  561.885112]         00 00 00 00 e0 50 
[  561.885123] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  561.886575] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.886589] Descriptor sense data with sense descriptors (in hex):
[  561.886594]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 ff 00 00 
[  561.886615]         00 00 00 00 e0 50 
[  561.886626] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  561.896777] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.896792] Descriptor sense data with sense descriptors (in hex):
[  561.896798]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  561.896820]         00 00 00 00 e0 50 
[  561.896832] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  561.900955] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.900970] Descriptor sense data with sense descriptors (in hex):
[  561.900975]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 ff 00 00 
[  561.900997]         00 00 00 00 e0 50 
[  561.901009] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  561.907657] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.907664] Descriptor sense data with sense descriptors (in hex):
[  561.907666]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  561.907673]         00 4f 00 c2 e0 50 
[  561.907677] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  561.917673] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  561.917682] Descriptor sense data with sense descriptors (in hex):
[  561.917685]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  561.917696]         00 00 00 00 e0 50 
[  561.917702] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available
[  562.068832] sd 6:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[  562.068849] Descriptor sense data with sense descriptors (in hex):
[  562.068854]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[  562.068877]         00 4f 00 c2 e0 50 
[  562.068888] sd 6:0:0:0: [sdb] Add. Sense: ATA pass through information available

```


Sessions
```
Session1:
	unix-user = '1000'
	realname = 'Nicolò Chieffo'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-11-28T09:10:59.632478Z'
	login-session-id = '4294967295'
Session2:
	unix-user = '1000'
	realname = 'Nicolò Chieffo'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-11-28T09:11:00.204347Z'
	login-session-id = '4294967295'

```

---

### Post by yelo3 on 2009-11-28
I'm sure I have a problem with policykit, because I can't do any action I could usually do (change user&groups, edit system networking)

---

### Post by Regenweald on 2009-11-28
Is gnome-policykit in your startup applications ? I removed policykit from my startup a while back and had some problems, this is the path to mine: /usr/lib64/policykit-1-gnome/polkit-gnome-authentication-agent-1
Hope it helps.

---

### Post by yelo3 on 2009-11-28
I have this running: /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

---

### Post by yelo3 on 2009-11-28
I tried to kill the process and run in again. I get this errors:
```
(polkit-gnome-authentication-agent-1:3761): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3761): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

```

---

### Post by Regenweald on 2009-11-28
Remove it, log out and in then re add it, is what i would try. I have no problems mounting an external 500gig fat system.

---

### Post by yelo3 on 2009-11-28
I reinstalled ubuntu and now it's ok

---

### Post by Regenweald on 2009-11-28
> **yelo3 said:**
> I reinstalled ubuntu and now it's ok
 
There's always that option :D

---

### Post by yelo3 on 2009-11-30
The problem is here again, I filed a bug in policykit-1
[https://bugs.launchpad.net/bugs/490322](https://bugs.launchpad.net/bugs/490322)

---

