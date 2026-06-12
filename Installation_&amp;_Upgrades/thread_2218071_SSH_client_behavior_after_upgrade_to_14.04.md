---
title: "SSH client behavior after upgrade to 14.04"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2014-04-19
I use the public key method for SSH authentication. Prior to 14.04, when I first initiate an SSH connection after logging in, a small window comes up asking for my passphrase. This is apparently a front end to run the SSH agent and do an ssh-add to decrypt my private key and add it to the running agent. Subsequently, I can initiate SSH connections with no further prompts. However, after upgrading to 14.04, none of this is working. If I try to ssh to another host, I am prompted (at the command line) for my private key every time. I can get things working by making sure the SSH agent is running and adding my private key via ssh-add, all using the command line, just like on non-Linux Unix systems, but the way this was working before is more convenient. Is there a way to get the former behavior in 14.04?

---

### Post by shochatd on 2014-04-20
I upgraded another computer (a laptop) also and found that what I called the "prior" behavior continued to work on the laptop after the upgrade. Both systems had ssh-agent already running on login, and both appeared to have valid /usr/bin/ssh-askpass symlinks set up. I suspected that it has something to do with gnome-keyring-daemon and studied this page:
[https://wiki.archlinux.org/index.php/GNOME_Keyring#Manage_using_GUI](https://wiki.archlinux.org/index.php/GNOME_Keyring#Manage_using_GUI)
Checking SSH_AUTH_SOCK on both machines, the laptop had something like:
SSH_AUTH_SOCK=/run/user/1000/keyring-.../ssh wherease for the desktop (with the problem), it was under /tmp. So I tried:
gnome-keyring-daemon -s as suggested in the above page. This changed SSH_AUTH_SOCK to be like on the laptop, so I tried logging out and back in again and found that SSH_AUTH_SOCK was still set to /run/user/1000/keyring-.../ssh. I did NOT do anything to my .bashrc. Now, I get the desired behavior on the desktop machine, i.e., when I try to ssh for the first time since login, I get the GUI dialog prompting me for my passphrase, and thereafter, my private key is obviously in the agent (no prompts for passphrase on subsequent ssh invocations).

---

