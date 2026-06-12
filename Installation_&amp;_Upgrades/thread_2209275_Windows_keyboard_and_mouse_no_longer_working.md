---
title: "Windows keyboard and mouse no longer working"
date: 2014-03-04
forum: Installation &amp; Upgrades
---

### Post by yousif-akbar on 2014-03-04
I recently installed ubuntu onto a second hard drive on my desktop, with Windows 8 installed on the first. Things were working well up until today when my keyboard and mouse stopped working on the windows side of things, but still work on ubuntu. I am using a Gigabyte motherboard and on another post it was recommended that IOMMU be set to enabled to solve the problem. I cannot find the setting on my BIOS, so I cannot tell if this is the issue, or if my mobo does not have this setting. I am using a mouse and keyboard with a wireless receiver, however even when using a wired one, I cannot get past the "picture" screen to get to the phase where I can type in my password. The circles that normally spin also don't show up as I log in. I could not find this exact problem elsewhere, so I figured I would post here. I don't know if it's relevant, but there may have updated windows to 8.1 yesterday. I don't remember, as I thought I had already switched, but there was an option to do so in my settings.

---

### Post by linuxonbute on 2014-03-05
[COLOR=#2A2A2A][FONT=Segoe UI]This appears to be a Windows 8 problem:(
See this:
[http://social.technet.microsoft.com/Forums/windows/en-US/06e9b341-0619-4085-acbf-e2f0133ca428/windows-8-keyboard-and-mouse-not-working?forum=w8itprohardware](http://social.technet.microsoft.com/Forums/windows/en-US/06e9b341-0619-4085-acbf-e2f0133ca428/windows-8-keyboard-and-mouse-not-working?forum=w8itprohardware)

One of the posts includes this:
> 
 Plugging the keyboard and mouse into other USB ports doesn't appear to fix the issue, however plugging in a **SECOND** keyboard and/or mouse works - ie the second keyboard is responsive even though the first one is still powered up, but apparently dead.[/FONT][/COLOR]> 
[COLOR=#2A2A2A][FONT=Segoe UI]once you have a working keyboard and/or mouse back, if you remove the keyboard device from Device manager, both keyboards stop working, but after a reboot the keyboards and mice are re-detected and the keyboard HID driver is re-installed.[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]Both keyboards and mice start working again. the original keyboard and mouse work fine after you unplug the second one(s).[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]It's not a permanent fix. For me, this has happened three times so far. I'm considering downgrading back to Windows 7 as that works fine. [/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]So, get a second keyboard (at least) or a cheap wireless keyboard/mouse combo and keep it handy.  But seriously Microsoft - this is an issue that appears to only affect Windows 8. it's a driver problem, not a hardware issue.  
[/FONT][/COLOR][COLOR=#2A2A2A][FONT=Segoe UI]

[/FONT][/COLOR]

---

### Post by phidia on 2014-03-05
Since IOMMU deals with RAM/memory I'm not sure that would cause what you are describing. If you have an old PS/2 keyboard mouse maybe that would get you over the Windows login issue?

---

