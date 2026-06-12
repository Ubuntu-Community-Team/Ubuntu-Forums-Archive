---
title: "installation of VMware 1.0.4 on Gutsy 32-bit"
date: 2007-10-25
forum: Kentucky Team - US
---

### Post by ScatterBrain on 2007-10-25
After struggling for two days trying to get VMware installed on 32-bit Gutsy, I was able finally able to get it going using the following steps.
 
*[COLOR=blue]Thanks a ton to **bkingx** for his help in locating the xorg-dev package. Without that, the installer fails to accept any serial numbers, and hence prevents VMWare Server from being properly installed.[/COLOR]*
 
**[COLOR=red]Installation of VMware Server:[/COLOR]**
1. Download VMware Server source from the [VMware website]("http://vmware.com/download/server/").
 
1a. Be sure to register to recieve your serial number(s)
 
2. Extract the archive to some location on your system
```
tar -zxvf VMware-server*
```3. Ensure that you have some prerequisites installed in order to compile these sources
 
```
sudo aptitude install build-essential linux-headers-`uname -r` xorg-dev xinetd
```4. CD to the newly create folder and run:
 
```
sudo ./vmware-install.pl
```5. Select all the default options.
 
 
**[COLOR=red]If you want the web based management user interface (MUI), then follow these additional steps:[/COLOR]**
1. Configure the default shell to be bash and not dash.
 
```
sudo ln -sf /bin/bash /bin/sh
```2. Return to the [VMware website]("http://vmware.com/download/server/") and grab the MUI archive.
 
3. Extract the files from the MUI archive.
```
tar -zxvf VMware-mui*
```4. CD into newly created directory and run:
```
sudo ./vmware-install.pl
```5. Accept all the defaults.
 
6). Access the MUI by pointing your browser to [**https://[your server ip address]:8333**]("https://%5Byour%20server%20ip%20address%5D:8333")
 
 
When all is said and done, you'll have VMWare running on the machine, and (assuming you installed the MUI as well) will be able to get some basic information about your server via a web browser.

---

### Post by Somatik on 2007-10-25
thanks!

---

### Post by Somatik on 2007-10-25
do you know how to enable remote login?

---

### Post by bkingx on 2007-10-25
> **Somatik said:**
> do you know how to enable remote login?

Somatik, 

SSH for Root is disabled be default.  Best practice is to create a normal user account and use sudo to run your commands.  

FWIW, though, you can enable remote login for root by editing /etc/ssh/sshd_config and change "remoterootlogin" to yes.
Save, then restart networking sudo /etc/init.d/networking restart

or if you are asking something else, please be a bit more specific.

You can feel free to contact anyone on the KY team on freenode, #ubuntu-kentucky

---

### Post by Somatik on 2007-10-25
Thanks bkingx but I was referring to remote vmware-server-console login

---

### Post by bkingx on 2007-10-25
If you have installed the MUI, then you should be able to using https://<serverip>:8333

---

### Post by ScatterBrain on 2007-10-25
> **Somatik said:**
> Thanks bkingx but I was referring to remote vmware-server-console login

You can either download the console client [from here]("http://register.vmware.com/content/download.html") and then install it.  Or, like bkingx said, you can use the MUI which has a download link that will pull the client directly from your server.

Once you have installed the console client, you can use it connect to the VMware server to control, create, delete or modify virtual machines.

I've always set the root password on the Ubuntu host, that way I can use root to logon to the server through the console client and have full control.  This isn't an Ubuntu recommended procedure, but I've done it out of old habits.

```
sudo passwd root
```

---

### Post by Somatik on 2007-10-26
I was able to log in using my normal user acount with the previous versions of vmware-server-console, this is not the case any more

---

### Post by ScatterBrain on 2007-10-26
> **Somatik said:**
> I was able to log in using my normal user acount with the previous versions of vmware-server-console, this is not the case any more

I'm able to do that without any problems.

Is it denying you access to logon, or preventing you from creating Virtual Machines?

---

### Post by Somatik on 2007-10-26
> **ScatterBrain said:**
> I'm able to do that without any problems.

Is it denying you access to logon, or preventing you from creating Virtual Machines?

it is preventing me to logon from an other machine in my network, local logon works.

---

### Post by ScatterBrain on 2007-10-26
> **Somatik said:**
> it is preventing me to logon from an other machine in my network, local logon works.

Really?

Can you logon with SSH?  As far as I know, VMware uses PAM for authentication.  So if SSH connections work, then VMware console connections should work.  (Unless something is totally messed up.)

Can you telnet to the console port on the machine:

```
telnet [server ip] 902
```

It should make a connection and identify itself as the "VMware Authentication Daemon"  If not, did you change the default console port when you installed VMware?

I'm running out of possibilities.... ;-)

---

### Post by Somatik on 2007-10-26
> **ScatterBrain said:**
> Really?

Can you logon with SSH?  As far as I know, VMware uses PAM for authentication.  So if SSH connections work, then VMware console connections should work.  (Unless something is totally messed up.)

Can you telnet to the console port on the machine:

```
telnet [server ip] 902
```

It should make a connection and identify itself as the "VMware Authentication Daemon"  If not, did you change the default console port when you installed VMware?

I'm running out of possibilities.... ;-)

remote telnet doesn't work, even local
remote ssh login works

fdb@mrblack:~$ telnet localhost 902
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
fdb@mrblack:~$ telnet 192.168.0.100 902
Trying 192.168.0.100...
telnet: Unable to connect to remote host: Connection refused
fdb@mrblack:~$ 

i'll try messing with the pam config files, there are no auth logs when I try to log in

---

### Post by Loranga on 2007-11-08
I can also confirm this problem (even if it is on Gutsy 64-bit desktop)

---

### Post by ScatterBrain on 2007-11-09
> **Somatik said:**
> it is preventing me to logon from an other machine in my network, local logon works.
> **Loranga said:**
> I can also confirm this problem (even if it is on Gutsy 64-bit desktop)


Did you change the default port for the console?  It should be 902.

Do you have a firewall on the machine?

Are you using an old version of the console client?  I know that this can cause problems - even though it should let you connect.

This is very odd.  I can do the telnet thing and it works just fine:

```
kcollins@graphite ~ $ telnet localhost 902
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 VMware Authentication Daemon Version 1.10: SSL Required, MKSDisplayProtocol:VNC 

```And to my production server:

```
kcollins@graphite ~ $ telnet onyx.nei.local 902
Trying 10.200.8.212...
Connected to onyx.nei.local.
Escape character is '^]'.
220 VMware Authentication Daemon Version 1.10: SSL Required, MKSDisplayProtocol:VNC 

```It sounds to me like either VMware isn't running, a firewall is blocking the connections or something went very wrong during the install/configuration.

---

### Post by DaZjorz on 2008-01-03
VMWare plugs itself into inetd by adding a line to /etc/inetd.conf. If inetd isn't installed, port 902 won't be accessible, so the solution is to install an inetd.

---

### Post by rh10023 on 2008-01-08
This is the error message when I try to connect to my vmware server with either my regular UNIX account or with the root account through the VMWare Server Console on my Windows computer.  I have the VMware server console software installed on an Windows XP Laptop that gets it's IP address assigned through DHCP.

-------
There was a problem connecting:

Cannot connect to host <hostname>: No connection could be made because the target machine actively refused it
-------

---

### Post by luke9511 on 2008-01-09
just found this guide after trying to get vmware installed and it help greatly and vmware runs ALOT faster in ubuntu than it did in windows thanks alot for the guide:-D=D>:biggrin:

---

