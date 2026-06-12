---
title: "A few problems"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by rgmaxey on 2007-03-13
Hello.

I'm new to the forum and new to Linux. I must say, I'm impressed with ubuntu; it's made Linux fun to use.

I've got it up and running on a dual boot with Vista and am making good progress, but there are a few issues I can't seem to resolve. Any help or advice would be greatly appreciated.

1. I can't get my networked printer (attached to a WinXP machine) working. I can navigate to the Windows computer to which the printer is attached, but I'm stopped at that point with the message: "Error returning browse list: NT_STATUS_ACCESS_DENIED." Is the problem on the Linux machine, or is there something I need to change on the Windows machine to allow access?

2. I can't get my built-in wireless connection working. System settings/network in Ubuntu show both my wired (eth0) and wireless (eth1) connections, but the wireless is marked as "disabled." I click on the button to enable it, but nothing happens.

3. What do I need to do to be able to view video on websites? I can't view the video on the CNN website, for example. I seem to recall something about mplayer ... is there some plug-in I need to install?

4. I can't play DVD's. I've installed the libdvd or whatever it's called, but all I get is sound and a blue screen. I think I know enough to know that the problem is missings codecs, but what do I need to do to get them?

Again, advice on any or all of these questions would be greatly appreciated. If I can address these four items, I think I'll be fully functional on Linux!

---

### Post by GreenHawkIA on 2007-03-13
2.  In order to fix that, you'll need to post more information.  What kind of wireless card are you using would be a good place to start?
3.  Here are a couple options to view video in your browser:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Mplayer32_with_Plugin_for_Firefox32](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Mplayer32_with_Plugin_for_Firefox32)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28VLC.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28VLC.29_with_plug-in_for_Mozilla_Firefox)
One uses MPlayer, one uses VLC, it's person preference.  Many sites use a flash player for video now - like YouTube - and to install that go here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
4. That same guide will have more information on enabling DVD playback.
There are tools that will automate these procedures for you, but how I first learned linux was following a command-line guide like that, and I still fall-back on those skills.  I highly recommend this route to learn your way around your new Ubuntu system.  Just read that page, it's very step by step, but will start to make you comfortable in the CLI.
Congratulations, and post if you have more questions.

---

### Post by panch0 on 2007-03-13
You don't need Flash to play Flash videos though. If you tell the browser to use MPlayer for Flash content, it will play Flash videos, and all the other Flash files (99.99% spam) will just show up as black squares and won't slow down your system.

---

