---
title: "Kubuntu 22.04.2 breaks screen resolution"
date: 2023-07-04
forum: Installation &amp; Upgrades
---

### Post by SeijiSensei on 2023-07-04
I have a mini-PC with an Intel video driver connected to my TV. Both support resolutions up to 4K. Kubuntu 22.04.2 used to work fine on this machine if I set the resolution down to something readable, usually 1280x720. Beginning a couple of days ago if I scale down the resolution I lose the panel at the bottom, and the whole screen seems slightly distorted. I think there was an update the other day that may have caused this effect. Reinstalling with 22.04.2 does not fix the problem. I'd like to try 22.04.1, but cdimage.ubuntu.com doesn't let me have that. Or maybe I could use an earlier Intel video driver. Any suggestions because this has been really maddening.

---

### Post by MAFoElffen on 2023-07-05
Are you using Xorg or Wayland?

I found 22.04 at archive.org: [https://archive.org/download/kubuntu-22.04-desktop-amd64/kubuntu-22.04-desktop-amd64.iso](https://archive.org/download/kubuntu-22.04-desktop-amd64/kubuntu-22.04-desktop-amd64.iso) ...But not 22.04.1.

---

### Post by SeijiSensei on 2023-07-05
I'm using whatever the default is. I've never had an issue with that before. I'll give that version a try.

Thanks.

---

### Post by MAFoElffen on 2023-07-05
How did that go for you?

I was thinking on this overnight... If you still have problems, then this would tell us which graphics engine you are using:
```

ps -e | grep -E -e 'tty' | grep -E -e 'x11|Xorg|wayland' | awk '{print $4}'

```
This would trace with i915 when and what is loaded and what the settings were:
```

grep 'i915\|drm\|intel\.' /var/log/syslog.1
journalctl -b -g 'i915' | grep .

```
Does your iCore CPU fall between Gen6 and Gen10? (GPU Gen6)?

---

### Post by SeijiSensei on 2023-07-07
I've resorted to a number of fixes to make the screen readable in 4K mode, which is the only one that works properly. I can upscale the size of the applications and such from the Kubuntu Settings manager. Never needed to do anything like this just a week or two ago.

---

### Post by SeijiSensei on 2023-07-07
> **MAFoElffen said:**
> Does your iCore CPU fall between Gen6 and Gen10? (GPU Gen6)?

It's a Celeron [N5105]("https://www.notebookcheck.net/Intel-Celeron-N5105-Processor-Benchmarks-and-Specs.514834.0.html") with a [Jasper Lake 24 GPU]("https://www.notebookcheck.net/Intel-UHD-Graphics-Jasper-Lake-24-EU-GPU-Benchmarks-and-Specs.514805.0.html"). It's described as Gen 11.

It's using Xorg.

Regular Ubuntu is up to 22.04.5, but Kubuntu only has 22.04.2 as the most recent point release.

I'm creating a 23.04 boot disk now. I'll see if that helps, or I'll give 23.10 a try. I don't like using non-LTS releases, but in this case it might be necessary.

---

### Post by SeijiSensei on 2023-07-07
Tried 23.04 and 23.10. Problem persists. I'm guessing it's a issue with the Intel video driver. Not really sure how or where to file a bug report. Manually reporting bugs through launchpad is a real pain. I'm guessing I should file against xserver-xorg-video-intel.

---

### Post by SeijiSensei on 2023-07-07
I've filed a bug report against xserver-xorg-video-intel.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/2026603](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/2026603)

---

### Post by #&amp;thj^% on 2023-07-07
> **SeijiSensei said:**
> I'm using whatever the default is. I've never had an issue with that before. I'll give that version a try.

Thanks.

i read the bug report, this happened to me as well on KDE and I just used the recommended work-around.
Workaround (for KDE):
[list]
    [*]Start up Ubuntu in Recovery Mode and get a root prompt
    [*]Hardcode the startup resolution in /etc/kde4/kdm/Xsetup (Change VGA to the proper name of your output, like DVI-1, LVDS, or whatever): 

  [*]xrandr --output VGA --mode 1024x768

    [*]Modify the mode 1024x768 to your preferred resolution in the above line [/list]

There may still be a brief 'out of range' error when the initial wallpaper is shown at full resolution, but then it shifts and login/normal operation follows. At least for me it did

---

### Post by MAFoElffen on 2023-07-07
I've have had to add more and more Linux kernel boot parameters to tweak certain settings that have been been an issue for my server (Intel iCore 10900):
```

mafoelffen@Mikes-B460M:~$ grep . /proc/cmdline
BOOT_IMAGE=/BOOT/ubuntu_2cwpns@/vmlinuz-5.19.0-46-generic root=ZFS=rpool/ROOT/ubuntu_2cwpns ro -- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on iommu=pt i915.enable_gvt=1 i915.enable_guc=2 i915.enable_fbc=0 systemd.unified_cgroup_hierarchy=0 libata.force=noncq vt.handoff=1

mafoelffen@Mikes-B460M:~$ grep 'GRUB_CMDLINE_LINUX_DEFAULT' /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="-- splash kvm-intel.nested=1 intel_idle.max_cstate=4 video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid intel_iommu=on iommu=pt i915.enable_gvt=1 i915.enable_guc=2 i915.enable_fbc=0 systemd.unified_cgroup_hierarchy=0 libata.force=noncq"

```
Where I add this:
```

video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid

```
That sets the video mode early in the kernel for it to use KMS (Kernel Mode Setting) to set the graphics mode during the kernel boot. That way it sets before the Desktop (DE) inits, which is very late in the Linux Graphics Layer process. 

Xorg and Wayland (graphics engines) do not start until after the DM (graphical login screens of GDM, SDDM, LightDM, etc). After the graphics engine loads, then the DE (Desktop Environment) loads. The GPU drivers do not start until the graphics engine phase, before the DE init's. 

I especially use that setting for people who get out-of-range errors before the DM starts (kernel messaging & splash). If set through the kernel KMS, then the DM and DE see's the KMS modes as a hint... So you both can see where setting it earlier in that process than just for the KDE DE would be beneficial right?

Sorry. Google: Alan Coopersmith... When I was a tester for OpenSolaris, back in 2005, he started teaching me how to support Xorg X11 for high-end GPU's... So, since then I've been supporting the Linux Graphics Layer, and helping people work out their graphics issues.  That is why I wrote the "Graphics Resolution" sticky in Installations & Upgrades, and why most of it is still relevant and useful today. It involves a lot more than just the later loaded graphics driver or the DE. 

Yes, expletive ('things') happens with the Linux i915 module. Intel provides the code for that, as they opensourced it. Sometimes that is a regression issue. Sometimes that is how a distro built their kernel, with the options they used. 

How you reported that is fine, [COLOR=#ff0000]just so it "gets reported"[/COLOR]... Launchpad, in their testing, if it is found to be another upstream part of the system, like module i915, or specific to KDE, will then transfer that on their own. LOL. 

Curious to see how this goes... As this is in one of my areas of interest.

---

### Post by SeijiSensei on 2023-07-10
I installed Debian 12 just to see how it works. It had the same screen resolution problem I encountered with Ubuntu. However, I was able to put the driver into 4K mode then use the scale control to enlarge the desktop. It maintained its shape within the boundaries of the screen. I would try it out again in Ubuntu, but I'd have to reinstall, and I'm curious about Debian 12. However I'm going to mark the thread SOLVED.

---

### Post by #&amp;thj^% on 2023-07-10
> **SeijiSensei said:**
>  I would try it out again in Ubuntu, but I'd have to reinstall, and I'm curious about Debian 12. However I'm going to mark the thread SOLVED.

I'm not sure you'll ever want to leave Debian 12....:)

---

