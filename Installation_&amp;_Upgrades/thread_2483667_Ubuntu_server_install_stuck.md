---
title: "Ubuntu server install stuck"
date: 2023-02-06
forum: Installation &amp; Upgrades
---

### Post by raveboy on 2023-02-06
Hi,

Writing in hope of finding a solution, i run a home lab on ESXi and until now I was able to deploy Ubuntu server vm's but now installation gets stuck at installing kernel.
Have tried multiple configurations and same result, no cpu activity for the vm and just rolling that bar at installing kernel
below a screenshoot

Any ideas would be more than welcomed ....

[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/74fbb233-0748-4472-948d-96e0c837ac4a[/IMG]
[FONT=Helvetica][subiquity/Debconf/apply_autoinstall_config subiquity/Kernel/apply_autoinstall_config subiquity/Zdev/apply_autoinstall_config subiquity/Late/apply_autoinsta11_config configuring apt curtin command in-target installing system[/FONT]
[FONT=Helvetica]curt in command install[/FONT]
[FONT=Helvetica]preparing for installation configuring storage[/FONT]
[FONT=Helvetica]running curtin block-meta simple' curt in command block-meta[/FONT]
[FONT=Helvetica]removing previous storage devices configuring disk: disk-sda configuring partition: partition-0[/FONT]
[FONT=Helvetica]configuring format: format-0[/FONT]
[FONT=Helvetica]configuring partition: partition-1[/FONT]
[FONT=Helvetica]configuring format: format-1[/FONT]
[FONT=Helvetica]configuring partition: partition-2[/FONT]
[FONT=Helvetica]configuring 1vm_volgroup: 1vm_volgroup-0[/FONT]
[FONT=Helvetica]configuring 1vm_partition: Im_partition-0[/FONT]
[FONT=Helvetica]configuring format: format-2[/FONT]
[FONT=Helvetica]configuring mount: mount-2[/FONT]
[FONT=Helvetica]configuring mount: mount -1[/FONT]
[FONT=Helvetica]configuring mount: mount -0 writing install sources to disk running 'curtin extract curt in command extract[/FONT]
[FONT=Helvetica]acquiring and extracting image from cp:///tmp/tmpugow2crg/mount[/FONT]
[FONT=Helvetica]configuring installed system[/FONT]
[FONT=Helvetica]running[/FONT]
[FONT=Helvetica]'mount --bind /cdrom /target/cdrom'[/FONT]
[FONT=Helvetica]running 'curt in curthooks'[/FONT]
[FONT=Helvetica]curt in command curthooks[/FONT]
[FONT=Helvetica]configuring apt configuring apt installing missing packages[/FONT]
[FONT=Helvetica]Installing packages on target system: ['efibootmgr', 'grub-efi-amd64" grub-efi-and64-signed[/FONT]
[FONT=Helvetica]'shim-signed'][/FONT]
[FONT=Helvetica]configurine iscsi service configuring raid (ndadm) service installing kernel[/FONT]
[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/97876aef-5858-4301-9c8f-5fb94cffb49b[/IMG]

---

### Post by MAFoElffen on 2023-02-06
What version of Ubuntu Server are you trying to install?

What config options are you giving the VM as resources?

I see you are installing as UEFI, but I didn't see an ESP partition created. Could you screenshot the partition options panel please?

---

### Post by raveboy on 2023-02-06
Thank you for your answer, below details requested:
ubuntu version: ubuntu-22.04.1-live-server-amd64 .... it was installing till now.
in terms of vm config:
- 32gb ram, 8 cores cpu
- reserve full ram
- 256 gb hdd, thick provisioning
- secure boot off, uefi on
- nic and cd-rom

PS: I even reinstalled ESXi on the NUC and I have a new error, attached

[https://imgur.com/a/vMnYCBX](https://imgur.com/a/vMnYCBX)

beats me why till now for last 2 weeks I deployed approx 10 linux vm's and now when I removed all of the vm's and decided on an OS it's not working.

---

### Post by MAFoElffen on 2023-02-06
My deployment strategy for VM's is a bit more conservative. I beta test for vSphere... But my go to is KVM.

What I usually allocate for an Ubuntu Server VM initially is 
- 4GB RAM for the install. `It needs less to run, but for the install it takes more...
- 25GB of disk. You can always add more later...
- 2 vCPU's. I can always add more later...

I install either Legacy or UEFI, whatever my tests are going to need. I install either with secureboot enabled or disabled.... Whatever my test case requires.

If UEFI,  in the partitioner, I ensure that it is going to create an ESP partition for EFI. If it is going to live for a while, I give it 750MB ESP, and create the other partitions myself.

I have noted that if UEFI, if you manually partition it and forget to create an ESP, that it will fail later...

What version of ESXi?

---

### Post by raveboy on 2023-02-06
ESXi 8.

After 6 hours of checking google, I found a thread with similar issue and the guy installed the server without NIC and it worked.
Did the same thing and the VM installed correctly ... I also allocated only 16Gb of ram

---

### Post by MAFoElffen on 2023-02-06
Which model NIC did it hang on?

---

### Post by raveboy on 2023-02-06
I got a good deal for the intel NUC 12Gen but will use it mainly for plex and docker contianers, nothing fancy

---

