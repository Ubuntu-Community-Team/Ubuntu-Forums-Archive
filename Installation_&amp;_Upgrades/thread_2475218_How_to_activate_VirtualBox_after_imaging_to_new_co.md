---
title: "How to activate VirtualBox after imaging to new computer"
date: 2022-05-19
forum: Installation &amp; Upgrades
---

### Post by boffin5 on 2022-05-19
Hi,
I use ubuntu on VirtualBox in order to run OpenFOAM CFD software on my Dell laptop.  Recently I got a new desktop computer,
and imaged the laptop drive onto it.  As I expected, VirtualBox doesn't work.  What do I have to do activate it on its new machine?
boffin5

---

### Post by TheFu on 2022-05-20
Since nobody has answered, thought I'd ask if the system changed hardware?  Network, CPU models or GPUs?
Did you reinstall virtualbox?  Also, are you using the version from the Oracle PPA?  I understand that is the preferred way, not from Canonical's repos.

I haven't used virtualbox at all since around 2014 and really stopped using it for daily VM needs in 2011.

BTW, what is the hostOS?  **lsb_release -d** will provide the answer on most LSB compliant Linux systems.

---

### Post by ActionParsnip on 2022-05-20
What OS is the host system please? you never said...

---

### Post by boffin5 on 2022-05-20
Thank you, theFu!

I really need to get Ubuntu running, and right now don't have a clue.

Here are the particulars:

Old system:
- CPU - Intel
- Windows 10 64 bit
- Graphics Processor - NVIDIA Quadro
- VirtualBox 6.1 was downloaded from Oracle

New system:
- CPU AMD Epyc
- Windows 10 64 bit
- Graphics Processor - AMD Radeon

Hoping you can give me guidance; the videos on the topic don't really address the same situation as mine.

boffin5

---

### Post by TheFu on 2022-05-20
And the host OS is?  ooop. Sorry. Windows.  I cannot help.  Good luck.  I thought Windows doesn't allow pulling a drive and cloning it for use in a different system.  A new install will install different code based on the CPU and GPU.  In theory, if the hostOS is the same and the version of virtualbox is the same, then the VM virtual-hardware just needs to be connected (perhaps the NIC changed on the host?) and it should all work.  I've moved VDI between systems a few times.  

More recently, I moved VMs that use a different hypervisor between Intel and AMD CPUs.  In the hypervisor per-machine settings, I had selected that the VM should look for a Core2Duo CPU. That caused issues until I changed it to "host CPU". Then it booted and ran fine. I did have to check the bridge name in the VM networking tab setup.  Different NICs could change the connectivity underneath.  And if the hostOS and guest don't use static IPs, I don't know.  I always use static IPs for both.

---

### Post by ActionParsnip on 2022-05-20
What happens when you launch the VM? What do you see?

---

### Post by boffin5 on 2022-05-20
Thank you ActionParsnip!
When I pick the green arrow to start Ubuntu, I get the black screen with the rolling setup, then it gets to "kernel panic - not syncing: Fatal exception in interrupt" and it just hangs.

---

### Post by TheFu on 2022-05-20
> **boffin5 said:**
> Thank you ActionParsnip!
When I pick the green arrow to start Ubuntu, I get the black screen with the rolling setup, then it gets to "kernel panic - not syncing: Fatal exception in interrupt" and it just hangs.

Check that the CPU model isn't set wrong in the VM settings for the vCPUs.

---

### Post by SeijiSensei on 2022-05-21
I'd delete the VM and reinstall. Trying to fix things like this is more trouble than it's worth.

---

### Post by boffin5 on 2022-05-21
Thanks for the help - partial Success!

I started VirtualBox, and picked 'file - check for upgrades.'  Then installed the latest version.  Now, VirtualBox starts, but when I start Ubuntu, all I get is a black screen.  I guess I'll search the forum for that problem.

---

### Post by TheFu on 2022-05-21
> **boffin5 said:**
> Thanks for the help - partial Success!

I started VirtualBox, and picked 'file - check for upgrades.'  Then installed the latest version.  Now, VirtualBox starts, but when I start Ubuntu, all I get is a black screen.  I guess I'll search the forum for that problem.

That's probably a GPU driver issue or the guest additions needs to be updated inside the VM.  check that sufficient vRAM is provided for the display.  I think the max is needed for desktops - 128MB.

---

