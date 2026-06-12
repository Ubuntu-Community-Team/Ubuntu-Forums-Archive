---
title: "safest way to remotely access ubuntu desktop"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by cpu2007 on 2013-04-29
I hope someone can guide me on this.

As far as I'm concerned, I've heard that the safest way to access ubuntu is through ssh.
but is it there any better way to connect to ubuntu from any os securely?

I've used tightvnc and after configuring my laptop to allow to be controlled, I can access it throught the network from xp,windows 7

however I'm not sure how secure this is.

What are the alternatives?

Thanks

---

### Post by darkod on 2013-04-29
Yeah, ssh would be the best way. You can run GUI session (X session) over it, although I haven't tried that yet nor tried to configure it.

For ssh make sure you disable root login, and alternatively configure it to use ssh keys only (which means no username/password option, make sure you are ready to use keys only before doing that).

That way no one without a key can connect to the machine. If the username access is enabled, someone might try to bruteforce guess the password.

---

### Post by cpu2007 on 2013-04-29
They key sounds a good way but what I'm wondering is that can I use the key on another different computer to access my laptop.
The intention is to be able to access my laptop from different places when required, (from a friend computer, work etc)
so, is it safe to have a key file and use that for the connection or a complicated password can be equally good?

---

### Post by darkod on 2013-04-29
I have used a key prepared on my work computer at home, and it worked. Of course, for accessing the same remote machine.

---

### Post by cpu2007 on 2013-04-29
thank you

will you be able to point out a tutorial that explain how to do this?

What I understand is that I have to use something like a ssh program (putty) then I have to install x11 on the machine I will be using to access ubuntu right?

---

### Post by steeldriver on 2013-04-29
You can tunnel VNC traffic over SSH - that way you can continue to use the tightvnc client from Windows if it works for you (instead of installing Cygwin/X)

For the default Desktop Sharing server (vino-server) that ships with the 12.04 Desktop Edition, you need to modify the config settings so that it only accepts connections on the loopback interface - that setting is not provided in the regular dialog box so you need to either install the dconf editor package and navigate to desktop -> gnome -> remote-access or modify it via the command line:

```
dconf write /desktop/gnome/remote-access/network-interface "'lo'"
```

After that the vino-server will no longer listen on external port 5900, instead you will need to start a putty session with an SSH tunnel from L5900 to localhost:5900 and point your tightvnc viewer at localhost:5900

If you are using tightvncserver instead of the default vino-server then ignore that (although the process is similar for tightvncserver, iirc you would add the [FONT=courier new]-localhost[/FONT] command line switch to the server invocation)

---

### Post by cpu2007 on 2013-04-30
Thank you for the guidance, I will try what you've suggested and post the results.

---

