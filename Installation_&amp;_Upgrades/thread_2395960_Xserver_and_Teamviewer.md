---
title: "Xserver and Teamviewer"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by fm394 on 2018-07-09
Hello,

I have SSH access to a virtual machine with Ubuntu 16.04 deployed in a server in my LAN, and I installed Teamviewer on it so that I can access it from anywhere.
When I connect to it through Teamviewer I can see the login page, but when I insert the password a system program problem is detected, the screen turns black for a couple of seconds and then I'm redirected back to the login page.
This is the content of the xsession-errors file:

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (1793) terminated with status 1
upstart: Disconnected from notified D-Bus bus
upstart: logrotate main process (1617) killed by TERM signal
upstart: unicast-local-avahi main process (1678) killed by TERM signal
upstart: update-notifier-crash (/var/crash/_opt_teamviewer_tv_bin_TeamViewer_Desktop.0.crash) main process (1681) killed by TERM signal
upstart: bamfdaemon main process (1727) killed by TERM signal
upstart: hud main process (1762) killed by TERM signal
upstart: unity-panel-service main process (1812) killed by TERM signal
upstart: indicator-bluetooth main process (1841) killed by TERM signal
upstart: indicator-power main process (1842) killed by TERM signal
upstart: indicator-datetime main process (1846) killed by TERM signal
upstart: indicator-printers main process (1853) killed by TERM signal
upstart: indicator-session main process (1854) killed by TERM signal
upstart: indicator-application main process (1907) killed by TERM signal



```

What's the problem? How can I fix it?

Thanks

---

### Post by TheFu on 2018-07-09
Sorry, I've never used teamviewer, so I can't help with this issue.

There are alternatives to provide GUI access from remote locations, securely, that don't trust a 3rd party.

* X11 forwarding using ssh. Doesn't work well with connections slower than 100Mbps.
* VNC over either an ssh tunnel or full VPN. vncserver has a built-in -localhost option to ensure only properly tunnelled connections work. 
* NX-base remote desktop - x2go is probably the best answer.

IMHO, x2go is the best solution and feels 2-3x faster than VNC.  x2go works over ssh, which is part of the NX protocol. With ssh-keys working, x2go will automatically authenticate and completely honors the ~/.ssh/config file like all ssh-base tools do.  The downside to x2go is that clients only work on desktop OSes; Widnows, OXS, Linux.

None of these solutions works well with heavy GUI DEs like Unity, Gnome3 or KDE.  Stick with XFCE, LXDE, or Mate, assuming you even need any DE at all.  I use openbox without any DE.

I use X11 forwarding on the LAN constantly (ssh -X), but my WAN connection isn't fast enough for this option.

I haven't used VNC since finding NX and avoid using solutions which require trusting some other cloudy provider.  And don't forget that all cloudy providers are juicy targets for attacks. [https://thehackernews.com/2017/12/teamviewer-hacking-tool.html](https://thehackernews.com/2017/12/teamviewer-hacking-tool.html)

---

### Post by fm394 on 2018-07-09
does x2go work if the server is behind a NAT?

---

### Post by TheFu on 2018-07-09
> **fm394 said:**
> does x2go work if the server is behind a NAT?

If ssh works, then x2go works. It uses an ssh tunnel over the existing ssh stuff.

If you do go with x2go, use a PPA for the client and server sides. Google will find the x2go website which has instructions for the different platforms.

---

### Post by fm394 on 2018-07-10
SSH works as long as I connect to the VM while I'm in my LAN, I installed Teamviewer because I need to connect to it from anywhere.

---

### Post by TheFu on 2018-07-10
> **fm394 said:**
> SSH works as long as I connect to the VM while I'm in my LAN, I installed Teamviewer because I need to connect to it from anywhere.

Open 1 tcp port on the router/firewall and forward  it into the static IP for the ssh server. Be certain to use ssh-keys, never passwords and it is important to block brute-force attacks after a few attempts.  DenyHosts, fail2ban, or highly restrictive firewall rules can handle that.

If you can't open an inbound port for ssh, you can use an ssh -r connect to a system outside to allow inbound connections.  A bi-directional VPN can fill the same needs.

The choice becomes whether you trust a third party with access to your systems/LAN or not.

---

### Post by fm394 on 2018-07-10
Thank you very much for the answers, I learned something new but it is not what I am looking for. 
I just need to access a stupid VM to do some stupid tests from anywhere, easy peasy. I do not want to set up a relay on a public address (I cannot do that btw) to redirect ssh traffic to and from my VM, and on top of that use some x11 forwarding technique.
For my case teamviewer is more than enough.
If no-one can help me with this problem I'll probably install teamviewer on my workstation in the LAN, so that I can access it from anywhere and then use x11 forwarding to access the vm with a gui.
Bad, but better then nothing.

---

### Post by TheFu on 2018-07-10
> **fm394 said:**
> Thank you very much for the answers, I learned something new but it is not what I am looking for. 
I just need to access a stupid VM to do some stupid tests from anywhere, easy peasy. I do not want to set up a relay on a public address (I cannot do that btw) to redirect ssh traffic to and from my VM, and on top of that use some x11 forwarding technique.
For my case teamviewer is more than enough.
If no-one can help me with this problem I'll probably install teamviewer on my workstation in the LAN, so that I can access it from anywhere and then use x11 forwarding to access the vm with a gui.
Bad, but better then nothing.

Give it another day, other volunteers here have used teamviewer.  They just need to see the thread.  I assume you've searched these forums already for all the other threads around teamviewer and those solutions didn't work?

Nobody here is paid, BTW.

---

### Post by fm394 on 2018-07-11
I know, and I really appreciated your help, it was very interesting in any case. Thank you :)

Indeed I browsed the threads related to Teamviewer, even if I don't think it's a Teamviewer specifically related issue. I found threads reporting very similar logs, but the suggested solutions did not work for me.

---

