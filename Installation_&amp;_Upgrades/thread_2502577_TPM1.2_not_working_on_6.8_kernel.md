---
title: "TPM1.2 not working on 6.8 kernel"
date: 2024-11-20
forum: Installation &amp; Upgrades
---

### Post by abhinavms on 2024-11-20
**System details**


[HTML]
$ uname -a
Linux RC240WZP2337Z0FD 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:   Ubuntu
Description:      Ubuntu 22.04.5 LTS
Release:          22.04
Codename:         jammy
[/HTML]

TPM is not working on the 6.8 kernel

[HTML]
$ tpm_version
Tspi_Context_Connect failed: 0x00003011 - layer=tsp, code=0011 (17), Communication failure
[/HTML]

On the same machine with 5.15 kernel, it is working fine
[HTML]
$ tpm_version>1V  
TPM 1.2 Version Info:
Chip Version:        1.2.66.1
Spec Level:          2
Errata Revision:     3
TPM Vendor ID:       ATML
TPM Version:         01010000
Manufacturer Info:   41544d4c
[/HTML]

[B]Logs
[/B][HTML]
$ sudo systemctl status trousers
× trousers.service - LSB: starts tcsd     
  Loaded: loaded (/etc/init.d/trousers; generated)     
  Active: failed (Result: exit-code) since Wed 2024-11-20 10:08:46 UTC; 32min ago 
  Docs: man:systemd-sysv-generator(8)    
  Process: 7838 ExecStart=/etc/init.d/trousers start (code=exited, status=135)

Nov 20 10:08:46 RC240WZP2337Z0FD systemd[1]: Starting LSB: starts tcsd...
Nov 20 10:08:46 RC240WZP2337Z0FD trousers[7838]:  * Starting Trusted Computing daemon tcsd
Nov 20 10:08:46 RC240WZP2337Z0FD tcsd[7945]: TCSD TDDL[7945]: TrouSerS ioctl: (25) Inappropriate ioctl for device
Nov 20 10:08:46 RC240WZP2337Z0FD tcsd[7945]: TCSD TDDL[7945]: TrouSerS Falling back to Read/Write device support.
Nov 20 10:08:46 RC240WZP2337Z0FD tcsd[7945]: TCSD TDDL[7945]: TrouSerS ERROR: write to device /dev/tpm0 failed: Timer expired
Nov 20 10:08:46 RC240WZP2337Z0FD trousers[7838]:    ...fail!
Nov 20 10:08:46 RC240WZP2337Z0FD tcsd[7945]: TCSD TCS[7945]: TrouSerS ERROR: TCS GetCapability failed with result = 0x1087
Nov 20 10:08:46 RC240WZP2337Z0FD systemd[1]: trousers.service: Control process exited, code=exited, status=135/n/a
Nov 20 10:08:46 RC240WZP2337Z0FD systemd[1]: trousers.service: Failed with result 'exit-code'.
Nov 20 10:08:46 RC240WZP2337Z0FD systemd[1]: Failed to start LSB: starts tcsd.
[/HTML]

dmesg log related to TPM

[HTML]
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.8.0-49-generic root=/dev/mapper/root-os ro console=tty1 console=ttyS1,115200n8 netcfg/do_not_use_netplan=true scsi_mod.use_blk_mq=1 net.ifnames=0 biosdevname=0 nomodeset noplymouth processor.max_cstate=1 intel_idle.max_cstate=0 ipmi_watchdog.timeout=3600 ipmi_watchdog.nowayout=1 fsck.repair=yes sunrpc.svc_rpc_per_connection_limit=32 libata.allow_tpm=1 intel_pstate=active cpufreq.default_governor=performance crashkernel=1G,high
[    1.002153] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.8.0-49-generic root=/dev/mapper/root-os ro console=tty1 console=ttyS1,115200n8 netcfg/do_not_use_netplan=true scsi_mod.use_blk_mq=1 net.ifnames=0 biosdevname=0 nomodeset noplymouth processor.max_cstate=1 intel_idle.max_cstate=0 ipmi_watchdog.timeout=3600 ipmi_watchdog.nowayout=1 fsck.repair=yes sunrpc.svc_rpc_per_connection_limit=32 libata.allow_tpm=1 intel_pstate=active cpufreq.default_governor=performance crashkernel=1G,high
[   16.346678] tpm_tis 00:07: 1.2 TPM (device-id 0x3205, rev-id 80)
[   16.388955] tpm tpm0: tpm_try_transmit: send(): error -62
[   22.619661] tpm tpm0: tpm_try_transmit: send(): error -62
[   32.859675] tpm tpm0: tpm_try_transmit: send(): error -62
[/HTML]

[HTML]$ sudo journalctl -xeu trousers.service
Nov 20 09:39:55 RC240WZP2337Z0FD systemd[1]: Starting LSB: starts tcsd...
&#9617;&#9617; Subject: A start job for unit trousers.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit trousers.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 152.
Nov 20 09:39:55 RC240WZP2337Z0FD trousers[13637]:  * Starting Trusted Computing daemon tcsd
Nov 20 09:39:55 RC240WZP2337Z0FD tcsd[13756]: TCSD TDDL[13756]: TrouSerS ioctl: (25) Inappropriate ioctl for device
Nov 20 09:39:55 RC240WZP2337Z0FD tcsd[13756]: TCSD TDDL[13756]: TrouSerS Falling back to Read/Write device support.
Nov 20 09:39:55 RC240WZP2337Z0FD tcsd[13756]: TCSD TDDL[13756]: TrouSerS ERROR: write to device /dev/tpm0 failed: Timer expired
Nov 20 09:39:55 RC240WZP2337Z0FD tcsd[13756]: TCSD TCS[13756]: TrouSerS ERROR: TCS GetCapability failed with result = 0x1087
Nov 20 09:39:55 RC240WZP2337Z0FD trousers[13637]:    ...fail!
Nov 20 09:39:55 RC240WZP2337Z0FD systemd[1]: trousers.service: Control process exited, code=exited, status=135/n/a
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; An ExecStart= process belonging to unit trousers.service has exited.
&#9617;&#9617;
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 135.
Nov 20 09:39:55 RC240WZP2337Z0FD systemd[1]: trousers.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; The unit trousers.service has entered the 'failed' state with result 'exit-code'.
Nov 20 09:39:55 RC240WZP2337Z0FD systemd[1]: Failed to start LSB: starts tcsd.
&#9617;&#9617; Subject: A start job for unit trousers.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit trousers.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 152 and the job result is failed.
[/HTML]

---

### Post by grahammechanical on 2024-11-20
What is your question? What is trousers.service? What is it expected to do. Have you read this?

[https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu](https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu)

> Based on Ubuntu Core&#8217;s FDE design, we have been working on bringing  TPM-backed full disk encryption to classic Ubuntu Desktop systems as  well, [COLOR=#ff0000]starting with Ubuntu 23.10[/COLOR] (Mantic Minotaur) &#8211; where it will be  available as an experimental feature. This means that passphrases will  no longer be needed on supported platforms, and that the secret used to  decrypt the encrypted data will be protected by a TPM and recovered  automatically only by early boot software that is authorised to access  the data. Besides its usability improvements, TPM-backed FDE also  protects its users from &#8220;evil maid&#8221; attacks that can take advantage of  the lack of a way to authenticate the boot software, namely initrd, to  end users

It seems that your motherboard has TPM 1.2. Has it been enabled in the UEFI settings?

Regards

---

### Post by abhinavms on 2024-11-20
> What is your question?
I am having a node with TPM 1.2 running Ubuntu 22.04. I need to upgrade to 6.8 kernel, but it looks like after upgrading to 6.8, the TPM module stops working. When the same node is switched to 5.15 kernel, suddenly the TPM module starts working. Therefore it looks like a kernel specific issue. I need help with trying to identify why the TPM 1.2 module is not working with the 6.8 kernel.

```

$ tpm_version
Tspi_Context_Connect failed: 0x00003011 - layer=tsp, code=0011 (17), Communication failure


# /usr/sbin/tcsd -f
TCSD TDDL ioctl: (25) Inappropriate ioctl for device
TCSD TDDL Falling back to Read/Write device support.
TCSD TDDL ERROR: write to device /dev/tpm0 failed: Timer expired
TCSD TCS ERROR: TCS GetCapability failed with result = 0x1087
```

> What is trousers.service? What is it expected to do

TrouSerS is a software stack that allows applications to communicate with a TPM. You can ignore the trousers part. The issue is that, tpm module is not working throwing the below error
```
$ tpm_version
Tspi_Context_Connect failed: 0x00003011 - layer=tsp, code=0011 (17), Communication failure
```

> Have you read this? 
[https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu](https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu)
I believe that is not relevant here as I am running 22.04 and TPM was already working with 5.15 kernel.

> Has it been enabled in the UEFI settings?
Since I am on a server, I can't access the UEFI settings. But I believe it is enabled due to 2 reasons
1. Switching to 5.15 makes the TPM module work
2. TPM device node exist
```
$ ls /dev/tpm*
/dev/tpm0

$ sudo dmesg | grep -i tpm_tis
[   11.398835] tpm_tis 00:07: 1.2 TPM (device-id 0x3205, rev-id 80)
```

Please let me know if you need any more info or logs to debug

Thanks!

---

### Post by abhinavms on 2024-11-28
Figured out the issue.. Looks like the read write hits are more on the new kernel causing the chip to crash. Adding a delay of 5ms to both TPM read & write resolved the issue... Still trying to identify the exact code causing more hits and add a delay there instead of having a overall delay

---

