---
title: "GPU reset issues when trying to wake from suspend on 22.04"
date: 2022-07-22
forum: Installation &amp; Upgrades
---

### Post by Raging_Cascadoo on 2022-07-22
**Problem Summary:**

A few weeks ago I performed a fresh installation of Ubuntu 22.04 due to a Nvme drive upgrade. Everything worked well except for the suspend. When resuming from suspend the majority of the times I would lose display completely or lose the display a couple seconds after the system came up. There were even a couple of occasions where I lost the display while using the system.

**Additional Info:**

[I]Hardware: 3800X, X370 taichi & 6600XT GPU. Also wanted to note that I never had this issue when using 20.04 with the same hardware.
Reddit post with steps taken when trying to troubleshoot:[/I] [https://www.reddit.com/r/Ubuntu/comments/w329tq/ubuntu_2204_suspend_resume_hell/](https://www.reddit.com/r/Ubuntu/comments/w329tq/ubuntu_2204_suspend_resume_hell/)

**Brief summary of troubleshooting:**

I used a laptop to connect to the machine via ssh to have a look at what happens when trying to resume from suspend. What I found on journalctl were GPU reset related errors whenever trying to resume from display. I tried a number of related fixes I found from posts with similar issues but nothing worked. I also noticed that via ssh, reboot or shutdown commands would make me lose the ssh connection as expected, however the system would then never shutdown or reboot but instead seemed to be in a hung state. I didn't have a serial connection at that point so hard shutdown was required and there was a lot of that happening! 

**I also came across this with similar issue but with a 6700XT:* [https://lore.kernel.org/regressions/99797fb7-76eb-9d86-ad2f-591243eca404@badpenguin.co.uk/](https://lore.kernel.org/regressions/99797fb7-76eb-9d86-ad2f-591243eca404@badpenguin.co.uk/)

**The "Fix":**

When I tried a kernel upgrade (5.18.12-051812-generic) suspend started working as it should and all the GPU related errors went away. I do have one issue since the kernel upgrade and that is when trying use virtual box it will freeze causing some other windows in the session to freeze. Once I kill all virtual box processes all other frozen windows/applications resume working which had me confused but this seems to have come about only after the kernel upgrade.

Did anyone else encounter this suspend and resume issue? Also would the upcoming 22.04.1 contain a kernel upgrade which may possibly have a fix for this issue? I would like to retain the stock kernel just to mitigate any issues that may crop up with running the latest kernel versions.

Below are some samples of the error taken from dmesg and journalctl which did go away after the kernel upgrade:

Journalctl:

```
Jul 19 15:09:23 MBLPC kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring sdma0 timeout, signaled seq=2833, emitted seq=2836
Jul 19 15:09:23 MBLPC kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process  pid 0 thread  pid 0
Jul 19 15:09:23 MBLPC kernel: amdgpu 0000:0f:00.0: amdgpu: GPU reset begin!
Jul 19 15:09:27 MBLPC systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Jul 19 15:09:28 MBLPC kernel: amdgpu 0000:0f:00.0: amdgpu: Failed to disable gfxoff!
Jul 19 15:09:28 MBLPC /usr/libexec/gdm-x-session[1845]: amdgpu: The CS has been rejected, see dmesg for more information (-16).
Jul 19 15:09:28 MBLPC kernel: amdgpu: Move buffer fallback to memcpy unavailable
Jul 19 15:09:28 MBLPC kernel: [drm:amdgpu_cs_parser_bos [amdgpu]] *ERROR* amdgpu_vm_validate_pt_bos() failed.
Jul 19 15:09:28 MBLPC kernel: [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to process the buffer list -16!
Jul 19 15:09:28 MBLPC kernel: [drm:dc_dmub_srv_wait_idle [amdgpu]] *ERROR* Error waiting for DMUB idle: status=3
Jul 19 15:09:33 MBLPC kernel: [drm:dc_dmub_srv_wait_idle [amdgpu]] *ERROR* Error waiting for DMUB idle: status=3
Jul 19 15:09:43 MBLPC /usr/libexec/gdm-x-session[1845]: amdgpu: The CS has been rejected, see dmesg for more information (-16).
Jul 19 15:09:43 MBLPC /usr/libexec/gdm-x-session[1845]: (II) event2  - USB Laser Game Mouse: SYN_DROPPED event - some input events have been lost.
Jul 19 15:09:43 MBLPC kernel: amdgpu: Move buffer fallback to memcpy unavailable
Jul 19 15:09:43 MBLPC kernel: [drm:amdgpu_cs_parser_bos [amdgpu]] *ERROR* amdgpu_vm_validate_pt_bos() failed.
Jul 19 15:09:43 MBLPC kernel: [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to process the buffer list -16!

```

Dmesg:

```
[  870.073534] amdgpu 0000:0f:00.0: amdgpu: GPU reset begin!
[  874.708070] amdgpu 0000:0f:00.0: amdgpu: Failed to disable gfxoff!
[  875.192581] amdgpu: Move buffer fallback to memcpy unavailable
[  875.192592] [drm:amdgpu_cs_parser_bos [amdgpu]] *ERROR* amdgpu_vm_validate_pt_bos() failed.
[  875.192816] [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to process the buffer list -16!
[  875.233785] [drm:dc_dmub_srv_wait_idle [amdgpu]] *ERROR* Error waiting for DMUB idle: status=3
[  880.109487] [drm:dc_dmub_srv_wait_idle [amdgpu]] *ERROR* Error waiting for DMUB idle: status=3
[  890.296488] amdgpu: Move buffer fallback to memcpy unavailable
[  890.296497] [drm:amdgpu_cs_parser_bos [amdgpu]] *ERROR* amdgpu_vm_validate_pt_bos() failed.
[  890.296708] [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to process the buffer list -16!
[  893.952810] amdgpu 0000:0f:00.0: [drm:amdgpu_ring_test_helper [amdgpu]] *ERROR* ring kiq_2.1.0 test failed (-110)
[  893.952909] [drm:gfx_v10_0_hw_fini [amdgpu]] *ERROR* KGQ disable failed
[  894.224730] amdgpu 0000:0f:00.0: [drm:amdgpu_ring_test_helper [amdgpu]] *ERROR* ring kiq_2.1.0 test failed (-110)
[  894.224831] [drm:gfx_v10_0_hw_fini [amdgpu]] *ERROR* KCQ disable failed
[  898.872216] amdgpu 0000:0f:00.0: amdgpu: SMU: I'm not done with your previous command!
[  898.872219] amdgpu 0000:0f:00.0: amdgpu: Failed to disable smu features.
[  898.872222] amdgpu 0000:0f:00.0: amdgpu: Fail to disable dpm features!
[  898.872223] [drm:amdgpu_device_ip_suspend_phase2 [amdgpu]] *ERROR* suspend of IP block <smu> failed -62
[  898.882557] [drm] free PSP TMR buffer
[  899.976700] [drm] psp gfx command DESTROY_TMR(0x7) failed and response status is (0x80000306)
[  899.997848] amdgpu 0000:0f:00.0: amdgpu: MODE1 reset
[  899.997850] amdgpu 0000:0f:00.0: amdgpu: GPU mode1 reset
[  899.997930] amdgpu 0000:0f:00.0: amdgpu: GPU smu mode1 reset
[  904.627674] amdgpu 0000:0f:00.0: amdgpu: SMU: I'm not done with your previous command!
[  904.627679] amdgpu 0000:0f:00.0: amdgpu: GPU mode1 reset failed
[  904.627788] amdgpu 0000:0f:00.0: amdgpu: ASIC reset failed with error, -62 for drm dev, 0000:0f:00.0
[  905.400355] amdgpu: Move buffer fallback to memcpy unavailable
[  905.400362] [drm:amdgpu_cs_parser_bos [amdgpu]] *ERROR* amdgpu_vm_validate_pt_bos() failed.
[  905.400497] [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to process the buffer list -16!
[  915.527813] amdgpu 0000:0f:00.0: amdgpu: GPU reset succeeded, trying to resume
[  915.528071] [drm] PCIE GART of 512M enabled (table at 0x0000008000000000).
[  915.528095] [drm] VRAM is lost due to GPU reset!
[  915.528997] [drm] PSP is resuming...
[  916.641712] [drm] failed to load ucode SMC(0x18)
[  916.641716] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000306)
[  916.641720] [drm] reserve 0xa00000 from 0x81f6400000 for PSP TMR
[  916.642154] [drm] psp gfx command SETUP_TMR(0x5) failed and response status is (0xFFFF0008)
[  916.642381] [drm] failed to load ucode SDMA0(0x0)
[  916.642383] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.642612] [drm] failed to load ucode CP_CE(0x8)
[  916.642614] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.642843] [drm] failed to load ucode CP_PFP(0x9)
[  916.642845] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.643073] [drm] failed to load ucode CP_ME(0xA)
[  916.643076] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.643304] [drm] failed to load ucode CP_MEC1(0xB)
[  916.643306] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.643534] [drm] failed to load ucode CP_MEC2(0xD)
[  916.643536] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.645939] [drm] failed to load ucode RLC_RESTORE_LIST_GPM_MEM(0x12)
[  916.645942] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.646169] [drm] failed to load ucode RLC_RESTORE_LIST_SRM_MEM(0x13)
[  916.646172] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.646399] [drm] failed to load ucode RLC_IRAM(0x14)
[  916.646401] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.646628] [drm] failed to load ucode RLC_DRAM(0x15)
[  916.646631] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.646858] [drm] failed to load ucode RLC_G(0x16)
[  916.646860] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.647312] [drm] failed to load ucode VCN(0x1C)
[  916.647314] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.816991] [drm] failed to load ucode DMCUB(0x22)
[  916.816995] [drm] psp gfx command LOAD_IP_FW(0x6) failed and response status is (0x80000203)
[  916.825607] amdgpu 0000:0f:00.0: amdgpu: RAS: optional ras ta ucode is not available
[  916.837114] amdgpu 0000:0f:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
[  916.837116] amdgpu 0000:0f:00.0: amdgpu: SMU is resuming...
[  916.837120] amdgpu 0000:0f:00.0: amdgpu: smu driver if version = 0x0000000f, smu fw if version = 0x00000013, smu fw version = 0x003b2800 (59.40.0)
[  916.837122] amdgpu 0000:0f:00.0: amdgpu: SMU driver if version not matched
[  920.264289] usb usb2-port6: Cannot enable. Maybe the USB cable is bad?
[  920.504265] amdgpu: Move buffer fallback to memcpy unavailable
[  920.504272] [drm:amdgpu_cs_parser_bos [amdgpu]] *ERROR* amdgpu_vm_validate_pt_bos() failed.
[  920.504495] [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to process the buffer list -16!
[  921.475189] amdgpu 0000:0f:00.0: amdgpu: SMU: I'm not done with your previous command!
[  921.475193] amdgpu 0000:0f:00.0: amdgpu: Failed to SetDriverDramAddr!
[  921.475194] amdgpu 0000:0f:00.0: amdgpu: Failed to setup smc hw!
[  921.475195] [drm:amdgpu_device_ip_resume_phase2 [amdgpu]] *ERROR* resume of IP block <smu> failed -62
[  921.475303] amdgpu 0000:0f:00.0: amdgpu: GPU reset(1) failed
[  921.477625] amdgpu 0000:0f:00.0: amdgpu: GPU reset end with ret = -62
[  921.496408] snd_hda_intel 0000:0f:00.1: refused to change power state from D0 to D3hot
[  931.512632] [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring sdma0 timeout, signaled seq=2836, emitted seq=2836
[  931.512886] [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process  pid 0 thread  pid 0
[  931.513112] amdgpu 0000:0f:00.0: amdgpu: GPU reset begin!
```

---

