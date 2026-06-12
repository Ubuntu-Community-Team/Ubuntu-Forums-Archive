---
title: "Remote X broke post upgrade to Gutsy"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by bmcatt on 2007-12-18
Finally was able to spend the time (not much time, yay!) to upgrade from Feisty to Gutsy. I'm still working on finding what's changed, etc., but one thing that's immediately noticable is that I've lost the ability to start a remote X session into my desktop.

Note - this was a configuration that was working immediately prior to the upgrade, so I know it's nothing that's changed network-wise.

I've got xhost configured properly and can, in fact, telnet in from the remote host to port 6000. I get a connection, but when I try and start an xterm, I get:
```
[1:11] bmc:~> xterm
Xlib: connection to "<hostname>:0.0" refused by server
Xlib: No protocol specified

xterm Xt error: Can't open display: <hostname>:0
```

[Hostnames deleted to protect the innocent :-)]

However, when I telnet:
```
[1:12] bmc:~> telnet <hostname> 6000
Trying 68.193.64.150...
Connected to <hostname>
Escape character is '^]'.
^]
telnet> quit
Connection closed.
```

Thus, as guaranteed, not a network routing / firewall issue.

Any assistance in fixing this would be most appreciated.

[On edit - yes, I know I can 'ssh -X' out, but I'd prefer to not do that. As I say, this was working pre-Gutsy, so I don't see why it shouldn't continue to work (possibly with some tweaking).]

---

### Post by bmcatt on 2007-12-18
Solved by disabling Xgl

```
> mkdir -p ~/.config/xserver-xgl
> touch ~/.config/xserver-xgl/disable
```

Evidently, the default Xgl settings (from /etc/X11/Xsession.d/98xserver-xgl_start-server) include '-nolisten tcp'. This also explains why it looked like I had two X servers running - one vanilla X and the other Xgl.

Have to say - this upgrade was not nearly as smooth as going from Edgy to Feisty.

---

