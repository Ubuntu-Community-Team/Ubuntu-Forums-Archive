---
title: "Horrific state to be in. Can't install Ubuntu due to HDD issues? HELP!"
date: 2020-11-18
forum: Installation &amp; Upgrades
---

### Post by misteranderson on 2020-11-18
[COLOR=#1A1A1B][FONT=&amp]Hello to everyone!
I am trying to install Ubuntu onto a machine with an installed Win10. In the "Something Else" section I can't find my windows C: drive so that I can delete it and say goodbye and install Linux
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]**[FONT=inherit]Relevant specifications:[/FONT]**
[FONT=inherit]A.[/FONT] BIOS Legacy, not UEFI
[FONT=inherit]B.[/FONT] 1 HDD which is Dynamic
[FONT=inherit]C.[/FONT] 4 partitions (1. system, 2. custom with my data, 3. and another custom one with my data which is for some reason split into 2 with the same letter in the disk manager, but not in the My PC window = 4 in total)
[FONT=inherit]D.[/FONT] The pen drive was formatted with a BIOS target.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]**[FONT=inherit]What I already know using google:[/FONT]**
[FONT=inherit]I.[/FONT] I can't use a dynamic Drive. I need a basic HDD. But how is it possible if I only have one HDD with Windows on it? How do I convert it if it needs to be empty, yet I need windows to do the conversion?
[FONT=inherit]II.[/FONT] My system can only handle 4 partitions at a time, so I guess I can't create one, which I understand, but at the same time why would I not be able to delete one and create one? (4 - 1 + 1 = 4)
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]**[FONT=inherit]What I want to know:[/FONT]**
[FONT=inherit]1.[/FONT] How do I make my pc just simply install Linux without windows? I am currently scooping my data 250GB to another PC with a "teaspoon" 8GB flash drive, so keeping the data is not a concern. In a day or so...[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][FONT=inherit]1.1[/FONT] Is it going to be enough if I just simply choose the option "Erase disk and Install" instead of "Something Else"? How will Linux handle the partitions? Will the hidden windows partition be visible for the Linux in this case, so it can wipe it away? How it will handle the partitioning? Create one big partition? Ideally, I would want to have 100gigs for the system and the rest for myself. I guess I can do this afterwards?[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][FONT=inherit]2.[/FONT] Or should I do something before doing Erase disk and Install? Some disk management on the windows I have still currently running? Wipe all except windows and do something with that?[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Thanks for reading and trying to help![/FONT][/COLOR]

---

### Post by tea for one on 2020-11-18
Before you do something that you may later regret, can you double check a few details?

It appears that you have made a Live DVD/USB to install Ubuntu - which Ubuntu flavour are you using?

Does your sound work?
Internet connection OK
Have you tested wireless (if it is present)?
Graphics OK?
Bluetooth?

You mention that your device is not UEFI, therefore it must be 10 years old or more?

Can you post full machine specs?

It is easy to replace Windows but it is better to check performance earlier rather than later.

---

### Post by misteranderson on 2020-11-18
Thanks for you answer!
I am using a relatively newwiish device. It is an Acer laptop with intel i3 5005, 8gigs of ram.
I am trying to install the standart Ubuntu 20.4 LTS.

In the msinfo32 i have also stated the following: BIOS Mode: Legacy. It lead me into thinking that i am using BIOS instead of UEFI.

I didn't test everything, but the graphics were great, internet and wifi great, sound great.

---

### Post by CatKiller on 2020-11-18
> **misteranderson said:**
> I am trying to install Ubuntu onto a machine with an installed Win10. In the "Something Else" section I can't find my windows C: drive so that I can delete it and say goodbye and install Linux

Windows doesn't shut down properly, it hibernates, so that booting it up doesn't take as long. That leaves any drives that Windows has touched in a dirty state, and Ubuntu won't go near them to prevent data loss. Windows calls it Fast Startup, and it's enabled by default and gets silently re-enabled by updates. Turn that off and shut Windows down properly, and the partitions should appear in the installer.

If you're nuking Windows so that you don't have to worry about it any more, you'll be better off switching to UEFI and GPT partitioning, and booting the installer in UEFI mode. BIOS is *very* old and very limited in many ways.

The default partition scheme for a UEFI Ubuntu install is to have a small FAT-formatted ESP and the rest as one big partition; swap files get used instead of swap partitions these days. If you want to divide that up, a smallish partition for / and the rest for /home is a relatively common way of doing it. You can do that from the Something Else dialogue. Or whatever scheme fits your needs.

---

### Post by dragonfly41 on 2020-11-18
Before jumping into the "Install Ubuntu" option FIRST use "Try Ubuntu" option.This allows you to see Ubuntu at work before any changes.

---

### Post by tea for one on 2020-11-18
I would recommend that you install in UEFI mode with GPT.

Here is a link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

How you boot the live session = How it is eventually installed
Boot in UEFI = Install in UEFI
Boot in Legacy = Install in Legacy

---

### Post by misteranderson on 2020-11-18
> **CatKiller said:**
> Windows doesn't shut down properly, it hibernates, so that booting it up doesn't take as long. That leaves any drives that Windows has touched in a dirty state, and Ubuntu won't go near them to prevent data loss. Windows calls it Fast Startup, and it's enabled by default and gets silently re-enabled by updates. Turn that off and shut Windows down properly, and the partitions should appear in the installer.

I dont have the option to disable it in the settings. It is not listed there. But i tried holding shift while shutting down, as suggested somewhere, i also tried [COLOR=#202124][FONT=arial]powercfg/[/FONT][/COLOR]hibernate off command in the prompt. Didn't help.

---

### Post by misteranderson on 2020-11-18
> **CatKiller said:**
> 
If you're nuking Windows so that you don't have to worry about it any more, you'll be better off switching to UEFI and GPT partitioning, and booting the installer in UEFI mode. BIOS is *very* old and very limited in many ways.


How could i do this?

---

### Post by CatKiller on 2020-11-18
> **misteranderson said:**
> I dont have the option to disable it in the settings. It is not listed there. But i tried holding shift while shutting down, as suggested somewhere, i also tried [COLOR=#202124][FONT=arial]powercfg/[/FONT][/COLOR]hibernate off command in the prompt. Didn't help.
I haven't used Windows in 15 years, so I can't help you find Windows settings.

It's also possible that your issue isn't (entirely) Fast Startup, but you might have your drive set to something other than AHCI in your UEFI. 
> **misteranderson said:**
> How could i do this?
When used with most burning tools, the Ubuntu installer is able to boot in either BIOS mode or UEFI mode - you pick which one from the motherboard's boot menu when you choose to boot it. I understand that some burning software forces you to choose when you're burning the image. Personally, I use Etcher, which is pretty straightforward, and doesn't make you choose.

You'll also need to turn off "Legacy" or "CSM" in your UEFI, which is the setting for making your UEFI pretend to be BIOS.

---

### Post by crip720 on 2020-11-18
Windows fast boot setting is windows power settings, it is usually also hidden behind something, check with google to find.

---

### Post by oldfred on 2020-11-18
All models of Acer also have a unique requirement of setting "trust" after install on Ubuntu entry. It will be shown as 'unknown'. Most have same or very similar install requirements.
Most also need UEFI update & if SSD, SSD firmware update.

And as many newer systems, you have to change from Intel RST/RAID to AHCI. Turn off fast boot in UEFI. Turn off Secure boot (but it needs to be on to set trust). 
In Windows turn off fast start up.

Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)


If you converted drive from basic to dynamic in Windows, you have to undo the dynamic partitioning.
Microsoft makes it easy to convert to dynamic, but has no undo. But some third party Windows tools may convert, but good backups required.
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by MartyBuntu on 2020-11-19
> **misteranderson said:**
> How do I make my pc just simply install Linux without windows?

Go into BIOS, disable secure boot and switch from UEFI to legacy BIOS.
Boot the Ubuntu Live DVD/USB.
The installer will take care of everything. Choose to use the entire drive for Ubuntu.

There's no reason to complicate this.

---

### Post by oldfred on 2020-11-19
If you switch from UEFI to Legacy, you break pre-installed Windows.

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012.
And Windows in UEFI mode only boots from gpt partitioned drives.

---

### Post by rbmorse on 2020-11-19
> **misteranderson said:**
> I dont have the option to disable it in the settings. It is not listed there. But i tried holding shift while shutting down, as suggested somewhere, i also tried [COLOR=#202124][FONT=arial]powercfg/[/FONT][/COLOR]hibernate off command in the prompt. Didn't help.

The fast startup option is under power options in the Windows control panel.  It's just above the option to enable hibernation, which should also be disabled in a dual-boot machine.

---

### Post by MartyBuntu on 2020-11-20
> **oldfred said:**
> If you switch from UEFI to Legacy, you break pre-installed Windows.

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012.
And Windows in UEFI mode only boots from gpt partitioned drives.

The OP sounds like they want "Linux Only".

---

