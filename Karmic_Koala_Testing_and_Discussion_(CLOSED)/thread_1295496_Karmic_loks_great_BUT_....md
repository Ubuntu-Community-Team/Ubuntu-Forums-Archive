---
title: "Karmic loks great BUT ..."
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by roberthr on 2009-10-19
I've been using Karmic since it came out of beta stage and I must say it's really nice and made some really good progress on Linux desktops. But it came with some very annoying regressions. Some are still present since Jaunty and some are new. So on my machines, I came across the following:

[LIST]
[*]Dell Vostro laptop still can't use touchpad and keyboard when booted from LiveCD. There is workaround with parameters that can be passed to kernel, but this is not really a solution. Everytime kernel is upgraded, those parameters are lost. Bug:[https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)
[*]GScan2PDF is great tool for scanning and manipulating PDFs but on Karmic, it can't save PDFs anymore!!! PDFs are the reason I use this tool with ADF scanner and suddenly it doesn't do what was made for :-( Bug: [https://bugs.launchpad.net/ubuntu/+source/gscan2pdf/+bug/424249](https://bugs.launchpad.net/ubuntu/+source/gscan2pdf/+bug/424249)
[*]Mplayer suddenly can't disable screensaver. This one is annoying when you watch movies and you have to move mouse all the time or disable screensaver. It worked ok since last week. Bug: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/439787](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/439787)
[*]Extremely slow printing of PDFs with Evince. It takes 25 minutes to print out the page on PDF that has only one page and is 8 Mb in size. I guess printing is problematic in all distros for ages. This should be finaly resolved because it's crazy I have to start Win in VirtualBox and print from there, if I need large PDF file printed fast!
[*]NetworkManager and 3G modems. It works great and it's simple but if you are out of country a lot, you don't have any option to choose which provider you want to connect to, or to check signal strength. Bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262232](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262232)
[*]Remote desktop connection where remote machine uses Compiz Desktop Effects. Forget it, you still can't use it. Bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)
[*]Evolution looks promising but it can't handle IMAP public folders on default Cyrus installations and still doesn't support IMAP IDLE extension that pushes new mail to clients. I know, this is not Ubuntu specific, but these days those features are a must.
[*]Firefox is still slow comparing to windows version running in Wine.
[*]OpenOffice default installation still doesn't install base package, needed if you do mailmerge from database or spreadsheet file.
[*]Folder Templates is still empty in Ubuntu. I know, everyone can make templates, but why not having some prepared for users migrating from Win?
[*]Novatel MC950 3G modems does not work anymore: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/128556](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/128556)
[*]Booting from LiveCD: You can't press any F key if you set your local language. If you managed to press F4 (safe graphic mode), setting is ignored but if you boot with default setting, you can't use display because it can't detect proper settings. That was with beta build, with RC build it is even worse since screen is just blinking in text mode while starting up until computer freeze.
[/LIST]
That's it. The list of most annoying bugs or missing features. I use Ubuntu for 4 years now and I love it but with every new realease I'm dissapointed. I do participate in bug reports and I know developers are working hard but please fix at least what's problem for years or wasn't broken until latest version.

---

### Post by popejeremy on 2009-10-19
> **roberthr said:**
> I've been using Karmic since it came out of beta stage

Karmic is still in beta stage. It has not come out of beta stage yet.

---

### Post by juancarlospaco on 2009-10-19
Use symlinks on template folders.

---

### Post by roberthr on 2009-10-19
I know it's still beta. But reading through bug reports and forums, some of those bugs won't be fixed and some of those missing features won't see light of day. I just wanted to stress out the most annoying things that bothers me since I ditched Windows completely.

---

### Post by xens on 2009-10-19
roberthr I totally agree with you, I have also been using Ubuntu for 4-5 years and I also have my bug-list that follow me through different releases...

I think that the 100 papercut experience should happen in every release, maybe also a quality label ?

---

### Post by psyke83 on 2009-10-20
> **roberthr said:**
> Dell Vostro laptop still can't use touchpad and keyboard when booted from LiveCD. There is workaround with parameters that can be passed to kernel, but this is not really a solution. Everytime kernel is upgraded, those parameters are lost. Bug:[https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)

I suspect you were editing legacy GRUB in an invalid way. For legacy GRUB, you shouldn't edit the kernel line directly in /boot/grub/menu.lst, as any custom changes won't survive a kernel upgrade. You should edit the DEFOPTS line and then run "sudo update-grub". Since Karmic uses GRUB2, the instructions are different - here's a quick guide:

Edit /etc/default/grub.

Change this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

To this (or whatever the appropriate kernel options are):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Blue"]i8042.reset i8042.nomux[/COLOR]"

```

Once you've finished editing, update the grub configuration:
```
$ sudo update-grub
```

All future kernels will then use the above kernel options.

---

### Post by roberthr on 2009-10-20
Psyke, thank you for Grub2 instructions. That helps a lot with Dell Vostro issues. And some others too, where customized kernel line has to be in place :-)

---

### Post by PC_load_letter on 2009-10-20
> **roberthr said:**
> 
[LIST]
[*]Dell Vostro laptop still can't use touchpad and keyboard when booted from LiveCD. There is workaround with parameters that can be passed to kernel, but this is not really a solution. Everytime kernel is upgraded, those parameters are lost. Bug:[https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)
[/LIST]


I did make a thread about this, except I was trying the Kubuntu Jaunty (correction below) liveCD!!!! This was on my Dell Vostro 1400 laptop.

**EDIT:** My bad, I doubled checked and it was Karmic, sorry.

---

### Post by roberthr on 2009-10-27
Two days left and none of mentioned problems got fixed. But I found some more, so I updated list  :-(

---

