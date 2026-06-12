---
title: "Nortel VPN in Interprid Ibex"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by the-saint on 2008-10-08
I just have upgraded from Hardy Heron to Interprid Ibex and am glad to see the VPN tab in the network manager but yet to figure out how to use it as when i click this tab and try configure VPN all the options are not active ...

Has anyone used the VPN option to success !!! will be glad to know how..

I have to connect to a nortel vpn with a RSA softid which i do using the contivity client in Windows. How do i do it in ubuntu

---

### Post by Sef on 2008-10-08
Moved to Ibex forum.

---

### Post by forumache on 2008-10-08
> **the-saint said:**
> I have to connect to a nortel vpn with a RSA softid which i do using the contivity client in Windows. How do i do it in ubuntu

You can't :(

I know that Novell made something like Turnpike plugin which allowed connection to a Nortel Contivity thing (but I don't think it had full support for all combinations).

---

### Post by the-saint on 2008-10-08
Thats so annoying would have login to windows just because of this

---

### Post by forumache on 2008-10-08
> **the-saint said:**
> Thats so annoying would have login to windows just because of this

At work I work on a Linux machine. The procedure when working from home is to use Nortel VPN from Windows, then use VNC, or better NoMachine to connect to the work machine (which runs Linux).

As I cannot stand using Windows just to remotely work from home, I used a workaround: I had a Windows in a virtual machine, used nortel vpn to authenticate, then logon on the work machine and open a ssh reverse tunnel to the home machine. Then I could close the virtual Windows, and just connect directly to the work machine through this reverse tunnel.

After some time, I thought of a better solution: I have a daemon using libyahoo2 library running on my work machine. It will appear in my list of friends in pidgin. It will accept commands only from me. From home, I send it an instant message: open tunnel! And the reverse tunnel will be open. It will remain open until either I reboot my home machine, my work machine, or I send another message to close the tunnel.

This way I don't need Nortel's VPN stuff anymore ;)

---

### Post by scorp123 on 2008-10-08
> **forumache said:**
>  After some time, I thought of a better solution: I have a daemon using libyahoo2 library running on my work machine. It will appear in my list of friends in pidgin. It will accept commands only from me. From home, I send it an instant message: open tunnel! And the reverse tunnel will be open. It will remain open until either I reboot my home machine, my work machine, or I send another message to close the tunnel. That sounds interesting (I mean the idea)! How did you implement this? Can you share more information? I'd need something like this too :)

---

### Post by forumache on 2008-10-08
1. Create a new userid on yahoo. This user will be used by the daemon only.

2. Download libyahoo2 from [http://libyahoo2.sourceforge.net/](http://libyahoo2.sourceforge.net/)

3. There is a simple client there. Modify it (I will provide the diff file tomorrow). You need to:
 - login to yahoo using your daemon yahoo userid
 - ignore any message coming from somebody else except your normal userid
 - recognize some phrases and react on them
You need to raise a tunnel, shut down a tunnel. Basically you execute ssh commands. (they will be in the code tomorrow). The only thing you need to be aware of is that you don't want your ssh command to ask for a password. In order to avoid passwords you need to create keys and put them on the home machine. Also the keys must be restricted from executing any command, we are using them just to forward ports.

4. Launch the daemon. The new userid will logon to yahoo. Choose to become friend with your daemon, it will appear in your list in pidgin/kopete/whatever. Give commands. It will execute commands on the work machine and it will create a tunnel to the home machine.

This little tutorial presumes that you are familiar with ssh, key authentication, port forwarding, modifying/compiling C code.

More to follow... tomorrow ;)

---

### Post by scorp123 on 2008-10-10
> **forumache said:**
>  More to follow... tomorrow ;) Cool :D  Looking forward to it :guitar:

---

### Post by forumache on 2008-10-19
Sorry for the delay. The recipe is following:

create a new yahoo user for your robot
download libyahoo2 version 0.7.6
modify the file sample_client.c (see mine in the attachment)
customize customization.h to suit your needs
compile
run the resulting yahoo executable

you'll see your robot coming online
when you start typing it will respond with "awaiting your command".
the commands are: "tunnel status", "tunnel up" and "tunnel down"

The robot will execute: ssh -fN tunnel when "tunnel up" is issued.
Of course, for this to work, you need to modify ~/.ssh/config to include:

Host tunel
Hostname your.ip.here
    User your_user_on_that_host
    RemoteForward 2222 localhost:22
    IdentityFile ~/.ssh/port_dsa

As you can see, you need to put your computer ip here, and the user you want to log on as. In order to skip password prompt we generated a DSA key (see ssh instructions) and instructed ssh to use that instead. Furthermore, the server key par does not allow this DSA key to be used for any commands, just to create ports forwarding.

Now:
the robot is running on the work computer
from your home computer you start pidgin/kopete
instruct the robot to open the tunnel
then you do a ssh -p 2222 localhost and it will logon to the work computer (because 2222 port is connected through a tunnel to work computer).

Need more info? Ask in this thread (or should I create a new one?).

---

### Post by scorp123 on 2008-10-19
Hey, thanks :D

I will try that stuff as soon as I have a little more time :)

---

