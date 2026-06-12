---
title: "Firewall for Ubuntu"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2005-11-10
I am using my Ubuntu-Laptop in a windows Network.

I know, there are not many nasty animals (Viruses, Trojan Horses, Worms, ...) for Linux at the moment. But anyway:

Is there a good firewall for Ubuntu?

What would you recomend?

---

### Post by frodon on 2005-11-10
I advise you [firestarter,]("http://www.fs-security.com/") it's easy to use and configure, and it's with a GUI.

---

### Post by Topsiho on 2005-11-10
You can find firestarter and install it using synaptic, or just install it with

sudo apt-get install firestarter

in a terminal (commandline)

Use your user password when a password is asked for .....

Tosiho

---

### Post by Roobert on 2005-11-10
[QUOTE=frodon]I advise you [firestarter,]("http://www.fs-security.com/") it's easy to use and configure, and it's with a GUI.[/QUOTE]

When I have Firestarter running, it's little icon is usually red, flashing in the upper-right panel area. I open the GUI up, and try to see what's going, but there's no indication it's flashing red because: a) I've been attacked by a remote computer, but the attack has been blocked, or b) I've been sucessfully intruded. Do I just keep on surfing, going on my merry way? Or does Fiestarter do something *else* when a successful attack has overcome it's defenses? 

Another question I have about Firestarter: Is it possible to have it autoload upon login? Currently, I have to go find it under Applications/System (I think).

Thanks!

---

### Post by frodon on 2005-11-10
Firestarter is running even if the GUI is not started, so you don't need to autoload the GUI, despites that if you still want to autoload the GUI on startup have a look here : [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)
Firestarter often print a lot of informations but that doesn't mean that someone is trying to intrude your computer, there's a lot of scan on internet, generally you shouldn't take care of that.
What make you say that someone as sucessfully intruded your computer ?

---

### Post by SickTwist on 2005-11-10
The only time the Firestarter GUI gives an alert is when something is blocked (which just indicates that the firewall is working). This feedback comes in handy if you're trying to troubleshoot why a network service isn't working (P2P program, Samba, SSH, etc) but isn't as important otherwise.

Also, Ubuntu has no firewall activated by default because no network services are running by default.

---

### Post by Roobert on 2005-11-10
[QUOTE=frodon]Firestarter is running even if the GUI is not started[/QUOTE]
Er, compare that statement to:

[QUOTE=SickTwist]...Ubuntu has no firewall activated by default because no network services are running by default.[/QUOTE]

:confused: I'm confused. Which is it?

[QUOTE=frodon]What make you say that someone as sucessfully intruded your computer ?[/QUOTE]

I didn't. I was wondering how I could tell whether a Firestarter alert meant I've been hacked into, or it made a successful block.

---

### Post by SickTwist on 2005-11-10
Ubuntu does not have the firewall activated after a default installation because there is nothing exposed that needs to be protected.

Firestarter is a GUI to configure the firewall that is part of the kernel. Once Firestarter has been installed, the firewall is automatically activated at every boot. However, you only start Firestarter (the GUI) if you want to configure the firewall.

Sorry if I confused you.

---

### Post by Roobert on 2005-11-10
[QUOTE=SickTwist]Once Firestarter has been installed, the firewall is automatically activated at every boot. However, you only start Firestarter (the GUI) if you want to configure the firewall.[/QUOTE]

AH, that clears it up. Thanks!

[QUOTE=SickTwist]Sorry if I confused you.[/QUOTE]

No worries!

---

### Post by frodon on 2005-11-10
lol, to explain you a little bit more, firestarter configures iptable and ipchain rules which are, as SickTwist told, built-in to the kernel.
So when you install firestarter ipchain and iptable rules are run as a service that's why your firewall is always running and activated at every boot, the goal of the GUI is to configure this rules and to see the traffic (or stop the firewall), for exemple i use often the GUI to allow the IP's of my friends who use my FTP server.
If you want to be sure of that, this command will show you the status of your firewall : ```
sudo /etc/init.d/firestarter status
```

Feel free to ask for more information, we will try to answer as clearly as possible ;)

---

### Post by phibuntu on 2005-11-12
Thanks all of you (especially frodon) for your answers to my simple question.
I am using firestarter now.

Many Test-Servers on the internet have approved that my system is now "very secure".

And I am very Happy :D

---

