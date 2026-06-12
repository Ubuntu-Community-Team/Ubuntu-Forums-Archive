---
title: "install different linux distro alongside existing"
date: 2024-03-09
forum: Installation &amp; Upgrades
---

### Post by ValentynPrumers on 2024-03-09
Hi!

I have installed kubuntu on my laptop using my entire hard drive. The installation process created 2 partitions. A fat32 /boot/efi and an ext4 / partition.

Now i want to try a different linux distro. But i dont want to lose my kubuntu. How do i approach this best?

Thanks :)

---

### Post by Rubi1200 on 2024-03-09
Backups, backups, backups BEFORE making any changes to drives/partitions.

Easiest way is to use pretty much any liveUSB that has GParted installed and use it to shrink the Kubuntu partition to make room for the new distro.

Two main things to be aware of:
1. you will likely need to do a manual install to make sure the new distro is pointed at the new partition you created
2. the new distro will install GRUB and be the one that controls booting not the GRUB of the Kubuntu install

How large is the hard drive and what is the new distro you want to install?

---

### Post by oldfred on 2024-03-09
Note if Ubunutu flavor or even based on Ubuntu it probbly will use the same installer & UEFI boot entry.
So you will only have one "ubuntu" entry in UEFI.
But grub should let you boot any install as long as installs are in same boot mode or all UEFI.

If you want your Kubuntu to be default, easiest way is just to boot into Kubuntu and reinstall grub.
sudo grub-install

You can manually edit /EFI/ubuntu/grub.cfg which has UUID of install it will use to boot into.
But Ubuntu locks ESP with mount in fstab. You can edit from live installer, or change defaults in fstab (but less security).

If not based on Ubuntu, then you probably get a grub or name of distribution  as boot entry in UEFI. It will be default but you can easily change boot order in UEFI with efibootmgr & -o parameter.
see
man efibootmgr
sudo efibootmgr -v # to see current order
sudo efibootmgr -o x,y,z

---

### Post by ValentynPrumers on 2024-03-10
> **Rubi1200 said:**
> Backups, backups, backups BEFORE making any changes to drives/partitions.

Easiest way is to use pretty much any liveUSB that has GParted installed and use it to shrink the Kubuntu partition to make room for the new distro.

Two main things to be aware of:
1. you will likely need to do a manual install to make sure the new distro is pointed at the new partition you created
2. the new distro will install GRUB and be the one that controls booting not the GRUB of the Kubuntu install

How large is the hard drive and what is the new distro you want to install?

Drive is 1TB, new system is Kali linux.

Can't i use KDE partition manager to shrink the current  / partition ? Or cant i do that because its mounted?

---

### Post by #&amp;thj^% on 2024-03-10
> **ValentynPrumers said:**
> Or cant i do that because its mounted?

That's a good guess, no partition tool will touch a mounted drive.

---

### Post by Rubi1200 on 2024-03-10
> **ValentynPrumers said:**
> Drive is 1TB, new system is Kali linux.

Can't i use KDE partition manager to shrink the current  / partition ? Or cant i do that because its mounted?

You cannot modify mounted drives/partitions No tool will allow that.

If I am not mistaken Kali should come with GParted. Boot it as a live medium and make the relevant changes to create space for the new install.

---

### Post by Frogs Hair on 2024-03-10
You can get look at many distros via web browser. They have a pretty good selection at the link.

 [https://distrosea.com/](https://distrosea.com/)

---

### Post by yancek on 2024-03-10
Since you appear to have a very limited knowledge in this regard, you might try installing Kali in virtual software or to a usb drive as explained in detail at the Kali site.

---

### Post by MAFoElffen on 2024-03-10
I would recommend the same.

Kali is Debian-based... so similar to a point. If it uses the old Ubiquity installer... Then after booting the live installer media in Try mode, you could use the command 
```

ubiquity -b

```
To start the installer without installing Grub... Then after the install, modify the /etc/default/grub file in your pre-existing Ubuntu Install, GRUB_DISABLE_OS_PROBER line to "false" to try to pick it up in the Grub2 menu. (***) 

I've done that in the past. Otherwise, I find if I want to try out multiple Distro's... If I don't necessarily need direct hardware access with that (I rarely do these days), then I install it as a VM Guest in KVM. That makes things more flexible and controllable. With KVM, I can also dynamically give it access to some hardware resources.

I used to do Contract IT Services, which Network Support was part of that. Kali runs well as a VM. Think also about learning WireShark, and building network taps & modular cable adapters. All of that was my go-to's on my laptop going onsite somewhere to diagnose problems.

NOTES: 
*** - I dont know how, yet, to do this method with the new Ubuntu  'ubuntu-desktop-installer' Flutter Installer. It's default behavior is  to install Grub2. I don't know yet how to turn that off. If someone has  found a way to do that with the new installer. Please share that.

---

### Post by ValentynPrumers on 2024-03-11
Thanks a lot! I think i will try to install it first as VM. Do you advice KVM over VirtualBox? Ive heard there were some problems with getting the wireless network card to work on a Kali VM. Is that true, or is that fixed?

(I also might want to create a windows 10 VM while i am at it, dont know if that changes anything)

---

### Post by MAFoElffen on 2024-03-11
I would indeed.

I used VirtualBox and VMware Player back in the late 2000s - early 2010's... KVM since before 2010. I have had to teach college students how to install VirtualBox (VB) for what they needed to do in their CS Courses, and to support it here in the Virtualization section... But, IMHO, VB is really bottom of the heap (limited) for what is possible with Virtualization... 

QEMU/KVM uses the hardware virtualization instead of software virtualization. It is a lot more flexible in what you can do and what you can replicate. Especially since you are getting into "networking" and penetration testing. You can replicate lot of different networking switches and devices within KVM and assign them to your hardware for access to outside resources, or isolated virtual networks to simulate what you want to try.

I would rather people have more than they need to explore the possibilities of what is possible, than fighting limitations trying to do what they need to do. Both directions are a ramp up to learn. Learn the concepts of virtualization in KVM, and they can be applied to other products. You will then see how limited those other products are.

I used KVM a lot while I studied and later taught CISCO CCENT and CCNA concepts for certifications. I could easily replicate a network, just like with CISCO Packet Tracer, in a real Virtual Network... Install WireShark and Kali Tools to test on, in a controlled environment, without the risk of bringing a Live Network down by "my testing". <<-- That is a consideration when you are trying out and learning how to use those tools.

I'm big on, if you learn how something works, how it should work, how things "look"... And what happens if you introduce problems... Then you can easier understand how to identify problems, correct and fix them.

Just some thoughts there to chew on.

Nowadays, I use KVM a lot for testing my code (how it runs on different platforms), testing DEV Cycle code, and for replicating "problems" people have here, to find solutions for them.

---

### Post by yancek on 2024-03-11
I've only used VirtualBox so can't offer a recommendation.  Might try both as they are available at the  Kali site.

[https://www.kali.org/get-kali/#kali-platforms](https://www.kali.org/get-kali/#kali-platforms)

Many users have 'problems' with network/wireless on Kali because they don't bother to read the documentation which specifically explains that networking is disables by default for obvious reasons.  Save yourself some problems and read the information at the Kali site from the link below.

[https://www.kali.org/docs/policy/kali-linux-network-service-policy/](https://www.kali.org/docs/policy/kali-linux-network-service-policy/)

---

### Post by MAFoElffen on 2024-03-11
Wireless on a laptop adds a limitation for all Virtualization Host platforms. It just adds a challenge. LOL

I mentioned I test DEV Cycle code... That includes for Ubuntu, Windows Insider Desktop and Server, VMware vSphere... For amd64, arm64, risc64, IBM System S360X, others. 

Windows Guests run well on KVM... Remembering this link for your Virtio Guest drivers: [https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers](https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers)

---

### Post by ValentynPrumers on 2024-03-11
Thanks a lot guys! I will read up on KVM and try to go that route :)

---

### Post by ubfan1 on 2024-03-11
Windows 11 23h2 guests are getting harder to set up, needing the software tpm stack (swtpm package) to install, but with the software present, virt-manager will automatically use it.  I normally just use straight kvm, but after failing to get the tpm stuff to work, tried virt-manager, and things just worked.  The tpm invocation virt-manager actutally used was **much** more extensive than the manual invocation I was trying.

---

### Post by MAFoElffen on 2024-03-11
Good point.

I use Virt-Manager to set things up... Then whatever to view it.

With TPM: Both physical or swtpm. I have had good luck with both ways.

---

### Post by ValentynPrumers on 2024-03-12
Been reading some about Kali as a VM. And it does seem you need an external usb WIFI card in order to get wifi to work. Is that true? My laptop does
not have an ethernet connection input. Only a wifi adapter and 4 usb-c (thunderbolt) ports.

If that's true, it might be more convenient for me to do an actual bare metal Kali install. As that seems to support buildin wifi adapters.

---

### Post by ubfan1 on 2024-03-12
My VMs automatically piggyback off the host's wireless. The connection isn't wireless as far as the VM is concerned, but I don't actually have ethernet.

---

### Post by MAFoElffen on 2024-03-12
As a VM, the host's WiFi connection will appear as a wired connection.

---

### Post by ValentynPrumers on 2024-03-13
> **MAFoElffen said:**
> As a VM, the host's WiFi connection will appear as a wired connection.

Does it appear as an ethernet connection?

Also do I absolutely need to setup a bridge? Like is advised here?

[https://ubuntuforums.org/showthread.php?t=2495946&page=2](https://ubuntuforums.org/showthread.php?t=2495946&page=2)

---

### Post by ValentynPrumers on 2024-03-13
> **ubfan1 said:**
> My VMs automatically piggyback off the host's wireless. The connection isn't wireless as far as the VM is concerned, but I don't actually have ethernet.

Did you get the buildin wifi card to work? Or did you use a usb wifi adapter?

---

### Post by ubfan1 on 2024-03-13
Used the builtin wifi of the laptop. To attach USB storage devices, I use a command:
sudo kvm -smp cores=4,threads=2 -cpu host -m 4096 -vga virtio -usb -device qemu-xhci,id=xhci -device usb-host,hostbus=$BUS,hostaddr=$DEV  $IMAGE
So maybe something like that might be necessary. No experience with USB wifi.

---

### Post by ValentynPrumers on 2024-03-15
Thanks!

Thats great to hear. Ive read a lot of people having trouble setting up the build in wifi adapter and needing to buy an usb wifi. I will try it soon and hopefully kali recognizes
my wifi adapter. 

Regarding the  external usb devices. I thought that could be handled by the gui (virt-manager)? I see you assign 4 cpu and 4GB of ram for your VM. Is that what
you recommend? My host has 20 cpu's and 16gb of ram. I don't have a glue what to assign to my VM. So any guidance is appreciated :)

---

### Post by ubfan1 on 2024-03-15
You can start 4 CPU and 4GB ram, and check how things are running with system-monitor.  Change things as necessary.  Not much experience with virt-manager, except for running the TPM required version of Win 11 (23h2) -- I'd failed doing that manually, but virt-manager worked with just the tpm software present (no special config, but  the command line it generated was quite complicated).

---

### Post by ajgreeny on 2024-03-16
> **ValentynPrumers said:**
> Does it appear as an ethernet connection?

Also do I absolutely need to setup a bridge? Like is advised here?

[https://ubuntuforums.org/showthread.php?t=2495946&page=2](https://ubuntuforums.org/showthread.php?t=2495946&page=2)

Yes it will show as an ethernet connection information, often enp2s0 on my VMs using KVM though the number may change depending on the situation and connection of your host.

If using the default NAT connection you can forget about setting up bridging; I've always used the NAT default on my VMs and have been using KVM for a few years now.

If you are setting up a VM as a server it may be necessary to use a bridged connection but I've never run a server so will leave others to advise you about that.

---

