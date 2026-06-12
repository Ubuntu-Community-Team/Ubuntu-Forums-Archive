---
title: "Ubuntu 22.04 system stopped working properly after upgrading from 22.04.3 to 22.04.4."
date: 2024-03-07
forum: Installation &amp; Upgrades
---

### Post by nkisnisci on 2024-03-07
Ubuntu 22.04 system stopped working properly after upgrading from 22.04.3 to 22.04.4. 
If I enter the system in maintenance mode, there is no problem, desktop works fine, but HDMI audio is not loaded and does not work. 
When I enter the system in normal mode, strange graphics appear on the desktop and the system cannot be controlled in any way. It is necessary to reset the system. 

 HW information in the system is as follows: 
System main board: MSI MS-7693 
CPU: AMD® Fx(tm)-8350 
GPU: AMD Radeon RX 560
Graphics : llvmpipe (LLVM 10.0.1, 256 bits)
Windowing System: X11
Gnome Version : 42.9

---

### Post by nkisnisci on 2024-03-07
I ran the *sudo apt install --reinstall xserver-xorg-video-amdgpu* command, then a blank screen appears, but alt-F2 also works as a console. 
So the system works but there is no desktop.

---

### Post by deadflowr on 2024-03-07
Can you check the running kernel?
```
uname -r
```
The update from one point release to another on the desktop version of Ubuntu usually coincides with an upgrade of the kernel version, 
in this case it would have upgraded from kernel 6.2 to kernel 6.5.

Luckily, you should still be able to boot into the old kernel,
basically when you start the machine press the ESC key to get the boot menu screen.
From there go down to the Advance Options submenu and enter that, and then from there you can choose a different kernel to log into with.
(Note, don't choose any marked as recovery unless you want to boot into the recovery system mode.)

If that fixes the issue, temporarily, you can try setting it to boot that old kernel by default.
This should give some help on how to set that up: [https://askubuntu.com/questions/1400257/how-can-i-always-boot-an-older-kernel-and-avoid-the-buggy-newer-one](https://askubuntu.com/questions/1400257/how-can-i-always-boot-an-older-kernel-and-avoid-the-buggy-newer-one)


Note that this would only be a temporary fix and you'll want to report the issue or something to get the newer kernel working.

---

### Post by nkisnisci on 2024-03-08
Thanks for your response. 
Kernel 6.5.0-21-generic and you are right, things got complicated after switching to kernel 6.5. 
Going back to the old version will cause update problems.

---

### Post by Impavidus on 2024-03-08
The 6.2 kernel just lost support on 22.04 (which is why you were upgraded to 6.5), so staying on 6.2 is indeed not a good option. Best to have this bug reported and hope for a fix. In the meantime, kernel 5.15 (the GA kernel, instead of the HWE kernel) will continue to be supported on 22.04, so that's another option – assuming it's modern enough for your hardware.

---

### Post by nkisnisci on 2024-03-08
Thank you for your response.
By the way, I made a new installation and also tried it with Radeon&#8482; Software for Linux® version 23.40.2 for Ubuntu 22.04.4 HWE, but I did not get any results.
I guess we'll have to wait.

---

### Post by deadflowr on 2024-03-08
> **nkisnisci said:**
> Thanks for your response. 
Kernel 6.5.0-21-generic and you are right, things got complicated after switching to kernel 6.5. 
Going back to the old version will cause update problems.
Why would it affect updates?

As I stated though, this would only be temporary anyway.
Just to try and get you a functional desktop.


> **nkisnisci said:**
> Thank you for your response.
By the way, I made a new installation and also tried it with Radeon™ Software for Linux® version 23.40.2 for Ubuntu 22.04.4 HWE, but I did not get any results.
I guess we'll have to wait. Is there a link where I can follow the bug?

See: [https://ubuntuforums.org/showthread.php?t=1011078]("https://ubuntuforums.org/showthread.php?t=1011078")

---

### Post by nkisnisci on 2024-03-09
I don't know if what's happening is a bug or not. When I test the GPU with GPUTest_Linux_x64_0.7.0 while in maintenance mode, there is no problem and the system runs smoothly in maintenance mode.

*amdgpu* related errors that occur when starting the system in normal mode;

16:57:35 pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
16:57:28 kernel: [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to initialize parser -125!
16:57:28 kernel: amdgpu 0000:01:00.0: [drm:amdgpu_ring_test_helper [amdgpu]] *ERROR* ring comp_1.0.1 test failed (-110)
16:57:27 kernel: amdgpu: rlc is busy, skip halt rlc
16:57:26 kernel: [drm:gfx_v8_0_hw_fini [amdgpu]] *ERROR* KCQ disable failed
16:57:26 kernel: amdgpu 0000:01:00.0: [drm:amdgpu_ring_test_helper [amdgpu]] *ERROR* ring kiq_0.2.1.0 test failed (-110)
16:57:26 kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process gnome-shell pid 1042 thread gnome-shel:cs0 pid 1077
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu: VM fault (0x01, vmid 3, pasid 32770) at page 173380013, read from 'TC2' (0x54433200) (8)
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu: VM fault (0x01, vmid 3, pasid 32770) at page 173380013, read from 'TC2' (0x54433200) (8)
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu:   VM_CONTEXT1_PROTECTION_FAULT_STATUS 0x06008001
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu:   VM_CONTEXT1_PROTECTION_FAULT_ADDR   0x0A5591AD
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu: GPU fault detected: 147 0x0d680801 for process gnome-shell pid 1042 thread gnome-shel:cs0 pid 1077
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu: VM fault (0x0c, vmid 3, pasid 32770) at page 0, read from 'TC0' (0x54433000) (72)
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu:   VM_CONTEXT1_PROTECTION_FAULT_STATUS 0x0604800C
16:57:14 kernel: amdgpu 0000:01:00.0: amdgpu:   VM_CONTEXT1_PROTECTION_FAULT_ADDR   0x00000000

---

### Post by ubfan1 on 2024-03-09
The 6.5 kernel requires the gcc-12 to compile its modules, but for Ubuntu 22.04, gcc-11 is the default, and gcc-12 normally is not present. This missing gcc-12 got fixed (weeks ago) by adding a dependency on the dmks package, so it gets pulled in along with the kernel.  Do you have the gcc-12 installed on your system (not as the default, just present)? If not, you can install it directly and maybe fix the issue.
sudo apt install gcc-12

---

### Post by nkisnisci on 2024-03-09
Thank you for your response.
I tried your suggestion but it was already installed.

[FONT=courier new]$ sudo apt install gcc-12 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
gcc-12 is already the newest version (12.3.0-1ubuntu1~22.04).
0 to upgrade, 0 to newly install, 0 to remove and 13 not to upgrade.

[/FONT]

---

### Post by nkisnisci on 2024-03-14
I think the problems are caused by the Graphics Card.
Updates and faulty installations caused problems in detecting the source of the problem. It worked properly in Recovery Mode and the tests ran smoothly, making it difficult to diagnose the problem.
As a result, trouble-free operation was achieved after replacing the new graphics card.

If I could more easily perform memory tests on the Graphics Card, problem detection would be faster.

Thanks to those who helped with their suggestions.

---

