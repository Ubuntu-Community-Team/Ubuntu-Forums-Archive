---
title: "Performance in a virtual machine."
date: 2013-12-15
forum: Installation &amp; Upgrades
---

### Post by Andrew_Lucas on 2013-12-15
Hi all,

As well as managing my own hardware, I also look after my family's PCs. For both them and me, Xubuntu provides a dependable base, free from risk of viruses, performance droops, etc., as well as being much more 'clean' in general: package management on Linux is much tidier than Windows, with central repos and commands to upgrade the entire system.

However, as much as I love Linux, I've had my arm twisted into dual booting. Windows is demanded by my University (i.e. because it doesn't operate an IMAP server, but uses Outlook Exchange), and some of my favourite Steam games haven't yet been ported (and given their age, probably never will be).

The annoying thing about dual booting, however, is it means that if you want to multitask - as we all inevitably do (e.g. I might play a game with music on in the background, or want to leave Skype signed in, or need access to a browser more function than IE) - then you have to duplicate, one for each OS.

I know WINE and other emulation offers a partial solution to the problem, but the fact of the matter is that WINE is cumbersome and awkward to use, and for every game I installed, I'd have to reconfigure it for that particular program. I don't regard it as a viable solution when dual booting is comparatively easy.

This got me thinking, however....what type of performance drop would I see by running Windows using something like VirtualBox? Obviously, having both OSes loaded would cause a performance hit, and having the OS run inside a VM rather than on bare metal would presumably add an extra abstraction layer which would slow things down...but would it be *really* bad? The computer I use for gaming is pretty solid: 8GB RAM, 8 core processor, AMD HD7850. Providing games would still be playable, I'm willing to compromise on their looks slightly, in order to gain that added  convenience of having only one OS to boot.

Can anyone see any other problems with this set up? Has anyone any first hand experience to offer? Plan would be to run Windows 7 Ultimate x64 in a VM, with Xubuntu 12.04 as the bootable OS.

Thanks!

---

### Post by jaime3 on 2013-12-16
Well I'm not really happy of the performance. Gaming in a virtual machine is very slow. Probably better solution is remote access a computer that you want to play games. I do that because I have servers so I use my laptop controlling all the server. I simply go back and forth. But in virtual machine more threads and cpu core is better and ram os love ram. But really running a window game in window in a vmware program it just not fast and you're not taking advantage of directx also. But how about remote access to physical gaming machine? I had some good fast computer but couldn't do it but I'm not a expert of vmware. Perhaps when in game mode simply reboot on that same machine it's much better and you'll take full advantage of you're system.

---

### Post by QIII on 2013-12-16
Hello!

A virtual machine is limited to the graphics performance allowed by the abstracted graphics hardware available.  Neither VBox nor VMWare provides anything at all comparable to your physical GPU.  That is, no matter how good your physical GPU the graphics performance will only be as good as the VM's virtual hardware -- which is to say not good at all.

Remoting has similar limitations.  RDP in to a Windows machine (and, by the way, you need the Pro or Ultimate versions of Windows to RDP ***in*** to them) is not going to be satisfactory because RDP does not offer good graphics performance by its nature.  VNC is worse.  NX is slightly better than RDP or VNC, but as far as I know there is no NX server solution for Windows -- NoMachine has been promising it for years and NoMachine NX 4.0 seems to be flapping in the breeze right now as far as development.  (If you do use NX, don't use passwords.  Use SSH keys.)

If you want to play Windows games, Windows on bare metal is really the best choice.  You might consider turning things around and running Windows with a Linux virtual guest or NXing from a Windows client to a Linux NX server if you want to have both running at the same time.

That may seem a bit heretical to some, but if it works it works.  Do what suits your needs, not what suits someone else's sense of propriety.

(Edit:  You could use a KVM (Kernel-based Virtual Machine) solution with Spice and virtualize *both* Windows and Linux, or use KVM in Ubuntu to virtualize Windows.  Spice can allow you "bare metal" access to your GPU, but KVM can present its own set of difficulties.)

---

### Post by 1clue on 2013-12-16
It depends a lot on your hardware.

Most modern hardware is set up for virtualization, both in the CPU and in motherboard features.  I make heavy use of virtualization on several platforms.  I consider KVM to be pretty good stuff for a small business.  VirtualBox is pretty much the same, only you have to run it from your desktop.

The good news:
[LIST=1]
[*]With modern hardware which supports virtualization, there is very little loss of performance.  The CPU is literally designed around virtualization, and so is the motherboard.
[*]The CPU usage is much better than you could imagine possible.  If all the guests demand cpu at once then it's terrible, but that rarely happens.  You get one guest grabbing CPU, it gets probably all of it, and everything else was idling anyway.  Then some other guest hits it hard, and so on.
[*]There's a LOT of virtualization engines out there, look for features and go that way.
[*]The virtual machines are easy to configure and are stable.  I've found that Windows 7 behaves better on KVM than it does on bare hardware.  There's a good reason for that, but won't get into it since it's really out-of-scope on your post.
[*]Microsoft and pretty much every other commercial software vendor knows about and has plans for virtualization.  Microsoft's licensing plans are constantly changing, but at one point when I needed one, I called their support line and the guy pointed me at one license specifically for virtualization.  Meaning it had more tolerance for changes of CPU type, that sort of thing.
[*]Moreover, the number you call from Microsoft doesn't even sell licenses.  If you ask, they'll direct you to a few authorized license retailers, but they're just there to help you figure out what best fits.
[/LIST]

The bad news:
[LIST=1]
[*]You need resources enough for ALL the VMs.
[*]RAM is required to satisfy all your currently *running* systems (host and guests) simultaneously.
[*]Disk is required to satisfy all your currently *configured* systems.
[*]Licenses for each guest are as though they are on real hardware.  Meaning if you have 3 Windows guests, you need 3 Windows licenses.  If you have Microsoft Office on two, ... you get the idea.  So in other words, this part only sucks if you use a commercial operating system.
[*]If you clone one Windows box and run both, that counts as two licenses for Windows, and two of whatever else is on there.
[/LIST]

Don't be afraid to contact Microsoft for help selecting licenses.  I've done it lots of times for my work.  Frankly I won't buy licenses any other way anymore.  Tell it to them straight, you plan to put it on a Linux VM, it's for school (discount!) and blah blah blah.  The fact you're contacting them means you want to be legal, and they'll point you at the most cost effective way to get what you want, legally.  I guarantee that there's no scenario they haven't already heard.

Real virtualization is the only way to go.  You get a stable operating system, you get to use your Linux box simultaneously, and everything works very smoothly.

---

### Post by SeijiSensei on 2013-12-17
> **Andrew_Lucas said:**
> Windows is demanded by my University (i.e. because it doesn't operate an IMAP server, but uses Outlook Exchange)

Do they support Outlook Web Access?  That only requires a browser.

There are also solutions to [get Thunderbird to work with Exchange]("http://debugge.com/thunderbird-and-exchange-without-imap-or-pop-support.db") even in situations where IMAP is not supported.  There's also an [Exchange plug-in for Thunderbird]("https://addons.mozilla.org/en-us/thunderbird/addon/exquilla-exchange-web-services/"), but it's not free.

---

