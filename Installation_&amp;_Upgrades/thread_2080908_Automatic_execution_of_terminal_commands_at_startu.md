---
title: "Automatic execution of terminal commands at startup"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by Loerie on 2012-11-05
Could someone please show an easy way to run terminal commands automatically during "start up"?

I know how to run terminal at start-up through "Startup Applications" but I am not technical enough to automate the running of terminal commands such as "sudo ....".

It could save a lot of hassle for beginner users.

---

### Post by The Cog on 2012-11-05
What kind of comands do you want to run, and what kind of "startup"? 

I see you want to do "sudo" commands. If you want these to run as the system boots (rather than when a users logs into the GUI) to do things such as setting firewall rules etc. then a common thing to do is to add a line calling the script to /etc/rc.local. /etc/rc.local is run as part of the system boot process. It will call the scripts with root's id so the script doesn't need to be called with sudo. But this also means that the scrip should be stored somewhere that only root can edit it, to prevent naughty users using it as a way to do things they shouldn't be able to.

If instead you are talking about running scripts as part of a user's login process then I'm not sure. It may be important to know which version of X/K/L/Ubuntu you are using.

---

### Post by darkod on 2012-11-05
Also, if we are talking about one or two commands, of course you can add them directly in /etc/rc.local above the 'exit 0' line.

If there are more commands, it's better to put all of them in a file (script) and call that script in /etc/rc.local.

---

### Post by Loerie on 2012-11-07
Thanks, folks. The version is Ubuntu 12.04-1
As mentioned, I am a user and not a technical expert.

I have added sudo iptables -L into the /etc/rc.local textfile using gedit but nothing happens after login.

The sudo iptables -L command is an example as there are other checks I would like to run after login from time to time.

---

### Post by darkod on 2012-11-07
I'm hardly an expert but I don't think that's a type of command you can expect output from.

It's one thing running it at the command line once you are logged in, but the rc.local runs the commands as root at the end of the boot process.

So, when you log into the system as USER you haven't even run the command as that user, so I don't think you will get any output waiting for you.

And as we said, the command are run as root by default so there is no need for sudo inside rc.local.

Do you have physical access to the machine, with a monitor and keyboard, or only remote/headless?

---

### Post by Loerie on 2012-11-07
Physical access.
I think what  you are saying is that rc.local is not the way to go.
Is there a simple way?

---

### Post by darkod on 2012-11-07
I didn't say that. I said I think that iptables -L is not a command for rc.local. That command produces a listing of iptables rules. You would put in rc.local something you want executed to do some job, not for listing data on the screen. rc.local will execute those commands regardless if someone is in front of the screen.

For example, if it helps you understand it better and assure you it's running the commands, do this simple test:
1. Try to ping this machine IP from another computer on the network. You should receive a reply (unless you have a firewall enabled).
2. Then in rc.local put few commands to flush the iptables rules, and set the INPUT policy to DROP:
iptables -F
iptables -P INPUT DROP
3. Reboot so that rc.local is executed. Try the ping now. There should not be a reply since the DROP will reject it.

Note that the above test will reject all traffic to that machine including remote access. That's why I asked if you are in front of it or not. After the test you will have to remove that DROP rule from rc.local and restart.

But if all this discussion is about iptables rules, there is a more convenient way to do it. Are you interested only in iptables or a mix of other commands too?

---

