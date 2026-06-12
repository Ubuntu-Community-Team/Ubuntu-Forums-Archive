---
title: "Ubuntu 18.04 detailed program install help"
date: 2018-09-29
forum: Installation &amp; Upgrades
---

### Post by 3drinks on 2018-09-29
Hi. I'm a new user to the software, been on reddit for help and was suggested I go here. I'm still learning and am trying (on a very ancient laptop, ha) to create a virtual environment that is not in windows or under Microsoft's thumb. As a daily driver, I'm close...but there's an important program I need that I would miss too much if I didn't have with me. Let me c/p my reddit post and findings for details of where I'm currently at;

[I]Me again (thanks for the loads of helping the other thread, btw! I've been enjoying this learning opportunity a lot). After the issues dual booting this on my main rig with Win10, I managed to find my old one. And boy is it old. To give you an idea, here's the stats;

* Acer aspire 5253
* AMD c-50 processor
* CPU speed 1000 MHz
* Dual monitor using a 24in vizio tv

Anyway, I did a fresh, clean install with only ubuntu, minimal install. Only mod so far is Discord. Now, from here I want to install Magic Online (maybe the skills I learn with this environment can be extrapolated to my main rig, heh). I went with this link to attempt to understand;

[https://www.reddit.com/r/magicTCG/comments/9cefm0/howto_install_mtgo_on_osx_and_linux_using_wine/](https://www.reddit.com/r/magicTCG/comments/9cefm0/howto_install_mtgo_on_osx_and_linux_using_wine/)

What do I need to find in the repository to make this work, from my current point? Wine? I searched that but didn't find anything. Docker? That sounds unsecure from the thread (but I may be misunderstanding) and I'm not sure I want to try that, but if it's safe then it's fine. At the same time, I'm not planning to take this anywhere as it has to stay plugged in anyway so I'm not sure how unsecure the docker method would really be to me, anyway.

Thanks in advance!![/I]

So I'm at the point that I got Lutris. Then when I found my program I ran into this;

```
*fixme:winediag:start\_process Wine Staging 2.21 is a testing version containing experimental patches.*

*fixme:winediag:start\_process Please mention your exact version when filing bug reports on* [*winehq.org*]([https://winehq.org)*.*](https://winehq.org)*.*)

*wine: cannot find L"C:\\\\windows\\\\system32\\\\winemenubuilder.exe"*

*err:wineboot:ProcessRunKeys Error running cmd L"C:\\\\windows\\\\system32\\\\winemenubuilder.exe -a -r" (2)*

*err:module:load\_builtin\_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.1: wrong ELF class: ELFCLASS64*

*err:winedevice:async\_create\_driver failed to create driver L"WineBus": c0000142*

*err:module:load\_builtin\_dll failed to load .so lib for builtin L"winex11.drv": libX11.so.6: wrong ELF class: ELFCLASS64*

*err:winediag:nodrv\_CreateWindow Application tried to create a window, but no driver could be loaded.*

*err:winediag:nodrv\_CreateWindow Unknown error (127).*

*err:appbar:initialize\_appbar Could not create appbar message window*

*err:ole:apartment\_createwindowifneeded CreateWindow failed with error 0*

*err:ole:apartment\_createwindowifneeded CreateWindow failed with error 0*

*err:ole:apartment\_createwindowifneeded CreateWindow failed with error 0*

*err:winediag:schan\_imp\_init Failed to load libgnutls, secure connections will not be available.*

*err:winediag:SECUR32\_initNTLMSP ntlm\_auth was not found or is outdated. Make sure that ntlm\_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.*

*err:winediag:gnutls\_initialize failed to load libgnutls, no support for encryption*

*fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub*

*fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub*

*err:winediag:nodrv\_CreateWindow Application tried to create a window, but no driver could be loaded.*
```

And that's where I left off. Once I get it set up on this old machine, my plan is to port it over to my good machine, basically using the bad one as my dummy machine.

---

