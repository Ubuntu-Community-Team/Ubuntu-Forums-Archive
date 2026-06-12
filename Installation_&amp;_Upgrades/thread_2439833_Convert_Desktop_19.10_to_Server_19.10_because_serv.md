---
title: "Convert Desktop 19.10 to Server 19.10 because server installation fails"
date: 2020-04-02
forum: Installation &amp; Upgrades
---

### Post by svh1985 on 2020-04-02
Hi,

I had some issues with installing the Ubuntu 19.10 Server installation (did not find the NIC drivers/firmware), so I had to install Ubuntu 19.10 Desktop instead.
Is there a way to convert my current Ubuntu Desktop to a Ubuntu Server?

ps. the source of my problem is of course that I could not install Server 19.10 due to driver, and it has me wondering why the server install disk doesn't ship the same drivers/firmware. And if there is a way to add them to the install disk for next time.

[I]Drivers:
[/I][I]Intel Wi-Fi 6 AX201
[/I]*Intel Ethernet Connection I219-V*


Thanks!

---

### Post by mörgæs on 2020-04-02
Hi, welcome to the fora.

Just use the normal commands to add the necessary server components to the desktop environment. For example, ```
sudo tasksel install lamp-server
``` installs the complete LAMP stack.

---

### Post by svh1985 on 2020-04-02
> **mörgæs said:**
> Hi, welcome to the fora.

Just use the normal commands to add the necessary server components to the desktop environment. For example, ```
sudo tasksel install lamp-server
``` installs the complete LAMP stack.

Thanks for the welcome &#128516; nice to be here!

I basically want to skim down the installation to only have the command line and docker running.
Do you know why the server install disk did not have the right drivers on board and how I can add the required drivers to the install disk? Maybe it's better to reinstall, if this is possible.

Thanks!

---

### Post by SeijiSensei on 2020-04-02
I wouldn't bother with 19.10 since its support window closes in the next six months.

20.04 will be available in a few weeks.  It is a release with "long-term support" and thus much better suited to servers.  If you use 20.04 now, just make sure to install updates routinely.

[http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/)

Usually Linux installs without a hitch on systems with Intel networking hardware.  Give it another try.

---

### Post by TheFu on 2020-04-02
Servers don't have wifi, so why bother to include those drivers?
The i219v  
[https://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop](https://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop)

Most people don't install non-LTS servers. 9 months of support just isn't worth our time.

i don't know how to make a desktop into a server, but you could start by removing all the GUi stuff.  The expected network configuration will always be different too since servers don't use network-manager.  There will be other funky things too.  it will always be a Frankenstein install.

LAMP server is far from the only sort used.  i have installed a "lamp-server" myself, but have been running Unix/Linux servers since around 1994.

Using the Ubuntu "Alternate" installer may provide what you seek.  IDK.

---

### Post by svh1985 on 2020-04-02
@SeijiSensei thanks, I'll use the 20.04 image &#55357;&#56836;

@TheFu, agreed, I don't need WiFi, only the i219v. I found that post before, but how can I slipstream that patched driver/firmware to the server install disk? Is that possible? I also found some ucode files.

---

### Post by TheFu on 2020-04-02
Last time I had a NIC driver problem, there was a way to manually load the driver. May have been only using the Alternate Installer.  

I don't know what "slipstream" means - outside of TV shows. 
Also don't know what "ucode files" are. Sorry.

---

### Post by svh1985 on 2020-04-02
With slipstreaming I mean add the driver to the install disk. The term is more common with Windows I guess.
It seems like the Alternate Installers do not exist anymore &#55357;&#56862; Can't find where to download them.

---

### Post by TheFu on 2020-04-02
[https://ubuntu.com/download/alternative-downloads](https://ubuntu.com/download/alternative-downloads) - was the top return by google. "Network installer"

---

### Post by svh1985 on 2020-04-02
I've managed to successfully install Ubuntu 20.04 Server using the daily build. Thanks for all the help!

@SeijiSensei, To update to the latest version have to run: 
[COLOR=#009900][FONT=Inconsolata]apt-get update
[/FONT][/COLOR][COLOR=#009900][FONT=Inconsolata]apt-get upgrade
[/FONT][/COLOR][COLOR=#009900][FONT=Inconsolata]apt-get dist-upgrade[/FONT][/COLOR][COLOR=#009900][FONT=Inconsolata]
[/FONT][/COLOR]
Right? And if 20.04 is officially released, how can I switch from the development branch to the production branch?

---

### Post by SeijiSensei on 2020-04-02
It will automatically become the production version as long as you keep the packages updated.

You don't really need to do dist-upgrade every time.  That brings in things like new kernel releases.  I usually just use "upgrade" normally, and "dist-upgrade" maybe once every week or two.

You don't need to do both in the same session.

---

### Post by svh1985 on 2020-04-02
Perfect, thanks for your help and the fast responses! &#55357;&#56836;

---

