---
title: "SSH hangs upon login"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by Eduardo Mercovich on 2008-09-03
Hello everybody.

I hope this is the right forum for this issue. I have searched but found nothing in the web or this forums. So if I used the wrong keywords, please apologize me and just tell me where is described. 

I have a fresh install of Ubuntu 8.04 in a Dell inspiron 1525 high (beautiful combination, by the way, everything except this worked perfectly, and the only remaining thing to try is the remote control) in Spanish.

The only problem I found is that I cannot access via ssh to another server. Just before login, it hangs the terminal.
Some facts: 

[LIST]
[*]After the initial prompt, if I put a wrong pass it prompts again, but when the right password is used, it just hangs there (I see nothing more that the cursor like if it is waiting) until the session is closed because it's inactive.
[*]Is not the server or a network problem, since other machine here can access OK.
[*]It happens with gnome-terminal or rxvt exactly the same.
[*]Once it's hanged, CTRL-C or CTRL-D does nothing. My only possibility is to close the terminal window.
[*]The same happens when I repeat the experiment from any tty (like when pressing CTRL-ALT-6).
[*]I can login perfectly well to my own machine, either using it's IP or localhost.
[/LIST]

I have installed:

> o@gont:~$ dpkg -l '*ssh*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nombre                 Versión               Descripción
+++-======================-======================-============================================================
un  libpam-ssh             <ninguna>              (no hay ninguna descripción disponible)
ii  libssh2-1              0.18-1                 SSH2 client-side library
ii  openssh-blacklist      0.1-1ubuntu0.8.04.1    list of blacklisted OpenSSH RSA and DSA keys
ii  openssh-client         1:4.7p1-8ubuntu1.2     secure shell client, an rlogin/rsh/rcp replacement
ii  openssh-server         1:4.7p1-8ubuntu1.2     secure shell server, an rshd replacement
un  rssh                   <ninguna>              (no hay ninguna descripción disponible)
ii  ssh                    1:4.7p1-8ubuntu1.2     secure shell client and server (metapackage)
un  ssh-askpass            <ninguna>              (no hay ninguna descripción disponible)
ii  ssh-askpass-gnome      1:4.7p1-8ubuntu1.2     interactive X program to prompt users for a passphrase for s
un  ssh-client             <ninguna>              (no hay ninguna descripción disponible)
un  ssh-krb5               <ninguna>              (no hay ninguna descripción disponible)
un  ssh-nonfree            <ninguna>              (no hay ninguna descripción disponible)
un  ssh-server             <ninguna>              (no hay ninguna descripción disponible)
un  ssh-socks              <ninguna>              (no hay ninguna descripción disponible)
un  ssh2                   <ninguna>              (no hay ninguna descripción disponible)

Any idea what could be happening here?
If there is more information needed to diagnose this issue, just ask me.

Thanks a lot for your attention. :-)

Regards...

--
EM

---

### Post by Pumalite on 2008-09-03
Go to Synaptic and Totally Remove openssh-client and openssh-server then reinstall.

---

### Post by Eduardo Mercovich on 2008-09-04
Hello Pumalite. 

The problem is that they are related to ubuntu-desktop and Synaptic asks me to uninstall it too... 

Is it any way to remove these packages without removing ubuntu-desktop?

Thanks a lot... 

--
EM

---

### Post by Eduardo Mercovich on 2008-09-04
> Go to Synaptic and Totally Remove openssh-client and openssh-server then reinstall.

After some help from a friend (gracias, Baby), I did it with:

```
sudo dpkg -P --force-depends openssh-client
``` and 
```
sudo dpkg -P --force-depends openssh-server
``` and 
```
sudo dpkg -P --force-depends ask-pass-gnome
```

After that, reinstalled ssh with 

```
sudo apt-get install ssh
```, and after some notices, I had to do 
```
sudo apt-get -f install 
```

But, sadly, everything seems to be just like before. 

Did I made a mistake? I didn't shut down or logged in again. Did I had to do that?

Thanks... 

--
EM

---

### Post by Peter09 on 2008-09-04
Check that the necessary ports for SSH on the server are open. You do need to open ports in your firewall and if necessary your router.

First try to connect locally to the machine ..

```
ssh -X name@localhost xterm
```

if that works then it points to a firewall / router problem.

The code below when entered into a terminal will list your open ports. SSH needs 22. 

> $ sudo iptables -L -n

---

### Post by Eduardo Mercovich on 2008-09-04
Hello Peter.

> **Peter09 said:**
> Check that the necessary ports for SSH on the server are open. You do need to open ports in your firewall and if necessary your router.

First try to connect locally to the machine ..
```
ssh -X name@localhost xterm
```

I can log in OK. 

> 
if that works then it points to a firewall / router problem.


The router is the same for both, so although even if something can be set up different for each machine, is not very probable... and I can't see it upon (my somewhat ignorant) inspection. Maybe the localhost rules are to blame...

> 
The code below when entered into a terminal will list your open ports. SSH needs 22.

$ sudo iptables -L -n


The output for iptables is

> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


I can see no specific port there... any documentation on how to interpret this for non-network-admins? :-) Reading the man pages is see that -n should show numeric output and I see nothing. Does this means that the port is not open?

More facts: an FTP connection (using gftp) that tries to use port 22 to be secure (that is, FTP via SSH I believe), hangs up just the same as in a terminal. The messages remain waiting upon loggin in...

Is any more useful info that I can gather or experiments to do?

Thanks a lot. :-)

--
EM

---

### Post by Peter09 on 2008-09-04
An easy way to manage your ports is to install firestarter which has a graphical front end, although I have not used it myself (its in the repositories). It looks like you have a problem on that port as ftp hangs as well.

I am unsure as to all the symptoms. Are you saying that one remote machine works while another does not?

---

### Post by Eduardo Mercovich on 2008-09-04
> **Peter09 said:**
> An easy way to manage your ports is to install firestarter which has a graphical front end, although I have not used it myself (its in the repositories). It looks like you have a problem on that port as ftp hangs as well.


I have just installed it. It says it can't run because eth1 is not ready, that I should check my internet connection. However, the connection is OK. 

Anyway, firestarter doesn't list any traffic restriction. :-(

> I am unsure as to all the symptoms. Are you saying that one remote machine works while another does not?

No, I'm sorry if I wasn't clear. I have 2 notebooks here, my old one (that can do ssh OK) and the new one (which cannot). Both connects wireless to the net through the same router (I am only using the old one to diagnose this issue).

--
EM

---

### Post by Peter09 on 2008-09-04
What command are you using to login, have you the same user name on both laptops?

use the -v switch to get a verbose output.

---

### Post by Eduardo Mercovich on 2008-09-04
> **Peter09 said:**
> What command are you using to login, have you the same user name on both laptops?

Yes. I do "ssh [email]user@lisa.dreamhost.com[/email]"

> use the -v switch to get a verbose output.

Ah! This could give us something tasty...

> 
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to lisa.dreamhost.com [208.113.148.19] port 22.
debug1: Connection established.
debug1: identity file /home/edumerco/.ssh/identity type -1
debug1: identity file /home/edumerco/.ssh/id_rsa type -1
debug1: identity file /home/edumerco/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch2
debug1: match: OpenSSH_4.3p2 Debian-9etch2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'lisa.dreamhost.com' is known and matches the RSA host key.
debug1: Found key in /home/edumerco/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/edumerco/.ssh/identity
debug1: Trying private key: /home/edumerco/.ssh/id_rsa
debug1: Trying private key: /home/edumerco/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password: 
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = es_AR.UTF-8


... and there it hangs up.

Any idea? Could it be the language? (sounds crazy, but in this world, anything is possible). Should I try to install and use the standard English language?

Thanks very much for your help Peter. :-)

--
EM

---

### Post by Peter09 on 2008-09-04
I guess you need to look at what is different between the two laptop machines, do they have a different language setup?

---

### Post by Eduardo Mercovich on 2008-09-05
> **Peter09 said:**
> I guess you need to look at what is different between the two laptop machines, do they have a different language setup?

```

Machine || OS          || Language
----------------------------------
Old     || Debian Etch || English
New     || Ubuntu 8.04 || Spanish
```

However, I logged-in in the new one with English as it's language and tried ssh with the same (unsuccessful) results...

Here is the output of ```
ssh -v
``` with English as language.

> 
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to lisa.dreamhost.com [208.113.148.19] port 22.
debug1: Connection established.
debug1: identity file /home/edumerco/.ssh/identity type -1
debug1: identity file /home/edumerco/.ssh/id_rsa type -1
debug1: identity file /home/edumerco/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch2
debug1: match: OpenSSH_4.3p2 Debian-9etch2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'lisa.dreamhost.com' is known and matches the RSA host key.
debug1: Found key in /home/edumerco/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/edumerco/.ssh/identity
debug1: Trying private key: /home/edumerco/.ssh/id_rsa
debug1: Trying private key: /home/edumerco/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password: 
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8


It hangs in the same point...

The installed packages are the same, except the ssh version that is newer in Ubuntu. But I doubt this is the problem, since many people would have found it before... don't you believe?

--
EM

---

### Post by Peter09 on 2008-09-05
I have done the same command and see some differences.
Can you show the log for the laptop that does work?

---

### Post by Eduardo Mercovich on 2008-09-05
> **Peter09 said:**
> I have done the same command and see some differences.
Can you show the log for the laptop that does work?

Sure. 

Erh... ejem... can you tell me how to check or view those logs? :-)

--
EM

---

### Post by Peter09 on 2008-09-06
Sorry, perhaps I wasn't clear. Can you do ssh -v on the laptop that allows to to login. Do the same as you did for the output of the problem laptop. We can then see where the differences are.

---

### Post by Eduardo Mercovich on 2008-09-08
> **Peter09 said:**
> [...] Can you do ssh -v on the laptop that allows to to login. Do the same as you did for the output of the problem laptop. We can then see where the differences are.

Oh, sorry, I didn't understood. 

The new (problematic) output is the previously reported in #10 and #12 (this thread). 

The old (working) one is this:

```

OpenSSH_4.6p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to lisa.dreamhost.com [208.113.148.19] port 22.
debug1: Connection established.
debug1: identity file /home/edumerco/.ssh/identity type -1
debug1: identity file /home/edumerco/.ssh/id_rsa type -1
debug1: identity file /home/edumerco/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch2
debug1: match: OpenSSH_4.3p2 Debian-9etch2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'lisa.dreamhost.com' is known and matches the RSA host key.
debug1: Found key in /home/edumerco/.ssh/known_hosts:20
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/edumerco/.ssh/identity
debug1: Trying private key: /home/edumerco/.ssh/id_rsa
debug1: Trying private key: /home/edumerco/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password: 
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US
Last login: Fri Sep  5 09:41:42 2008 from 190.55.177.174

```

The last line and what follows (the welcome message) are never seen in the new laptop.

At first sight, the only diff I see are 
[LIST]
[*]the local ssh version (*4.6p1 Debian-5* in the old and *4.7p1 Debian-8ubuntu1.2* in the new one) and 
[*]the environment (last line, *LANG = en_US* in the old and *LANG = en_US.UTF-8* in the new).
[/LIST]

I doubt the local version can be broken. Could the environment be the problematic issue?

Thanks a lot for your patience and perseverance. :)

Regards...

--
EM

---

### Post by Peter09 on 2008-09-09
Hi,
yes it is difficult to see anything in that which could be a problem. Must admit I am puzzled.

Are there any logs on the server which may give a clue. What does syslog say?

---

### Post by Eduardo Mercovich on 2008-09-11
> **Peter09 said:**
> Hi,
Are there any logs on the server which may give a clue. What does syslog say?

Hi Peter. 

I've been looking at how to check what syslog say, but I could only find that there are many logs in the server (found that in /etc/syslog.conf). 

Which one should I look at? 

While I use Linux since some time, I don't know very much about the inside of the system (or at least, about syslog). So please, don't bother yourself writing full instructions, but if there is some place or documentation just point me there and I'll do my homework. :-)

Thanks again... 

--
EM

---

### Post by cpetercarter on 2008-09-11
It seems from the output of ssh -v that the remote machine is accepting your connection, authenticating your password login, and then hanging. In other words, I wonder if the problem is on the remote machine rather than on yours. Are you able to contact the owner/administrator of the remote machine to see if they can sort things out?

---

### Post by Eduardo Mercovich on 2008-09-11
> **cpetercarter said:**
> [...] In other words, I wonder if the problem is on the remote machine rather than on yours.

The remote machine is working OK with any other clients, so it seems that the problem is in my new laptop. I can login even with my old laptop from the same wireless connection in my studio, so it's not a network problem neither.

Also, I doubt the host provider has set any kind of filters.

>  Are you able to contact the owner/administrator of the remote machine to see if they can sort things out?

I did that already, and they report that the services are running all OK, which is coherent with the fact that I can login from other machines... 

It is really weird... 

--
EM

---

### Post by Eduardo Mercovich on 2008-09-16
Hello.

More information. The same happens when I try to login via SSH to any other machine. This is, the hang up of the SSH console is independant from the destination machine, and completely dependant from the originating computer (the new laptop).

Thanks to all for your time and dedication. I am sure we will be able to diagnose this issue with SSH. :-)

Regards...

--
EM

---

### Post by Eduardo Mercovich on 2008-09-16
Hello.

More information: the same happens when I try to login via SSH to any other machine. This is, the hang up of the SSH console is independant from the destination machine, and completely dependant from the originating computer (the new laptop).

I would like to thanks again all of you for your time and dedication. Even if we still can't diagnose this issue with SSH, I'm sure we will be able to do it in the end. This community is the best component of any Ubuntu installation. :-D

Regards...

--
EM

---

### Post by Peter09 on 2008-09-16
All I can suggest is that you go through the ssh configuration file in detail. Also check that the user id that you are logging in with is correct. (have you the same user id on both machines, could this cause a problem)?

---

### Post by Eduardo Mercovich on 2008-09-17
> **Peter09 said:**
> All I can suggest is that you go through the ssh configuration file in detail.

Which one? In the local machine, or the remote?

The local seems to be OK, since I can make ssh to myself without problems. 

> Also check that the user id that you are logging in with is correct. (have you the same user id on both machines, could this cause a problem)?

I have the same user in both machines. To check if that could be a problem I created a new user, logged in and made SSH to the remote machine: the same hangup after the password... :-(

--
EM

---

### Post by Peter09 on 2008-09-17
Whatever the problem it suggests that it is the local machine as you indicate that you cannot login to other servers (am I correct?).

So I was suggesting that it may be some difference in the config file on the local machine.

---

### Post by Eduardo Mercovich on 2008-09-24
> **Peter09 said:**
> Whatever the problem it suggests that it is the local machine as you indicate that you cannot login to other servers (am I correct?).

So I was suggesting that it may be some difference in the config file on the local machine.

It seems that is not the config file. 
Thanks again to you, that have discovered the thread [http://ubuntuforums.org/showthread.php?p=5836384#post5836384](http://ubuntuforums.org/showthread.php?p=5836384#post5836384), now we have some more valuable information. 

If I connect wireless, SSH doesn't work, as described. But if I plug the cable... voila! It works flawlessly. 

So it seems that it is, somehow, a matter of the wireless connection, and the same as bugged in [https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816](https://bugs.launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/+bug/259816) (reported in the mentioned thread).

Since I am fairly new to this forums, what is the best way for all? Do you suggest to follow this in the other thread, or here?

Also, a tiny detail while we work this out: Putty works OK, even with a wireless connection. 

Thanks a lot... :-)

--
EM

---

