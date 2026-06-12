---
title: "Creating a local update server ||| TYPE : FTP"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by linuxyogi on 2011-06-04
Hi,

I am planning to migrate to a new broadband plan which promises greater speeds but at the cost of limited upload/download.

I am running Lucid on one of my PCs & Debian 6 on the other.

Now that I have a limited upload/download window I want to install Lucid on the PC now running Debian & share the updates between the two.

I did find some threads regarding the subject but they seem a bit complicated to me.

I just want to create a ftp server on one of the PCs and add an entry pointing to that on the other one.

Thanks in advance.

---

### Post by oldfred on 2011-06-05
Do not know about your own FTP server. Some alternatives. If just two systems you can copy downloaded debs.

aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

Location of downloaded debs
/var/cache/apt/archives/

Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by linuxyogi on 2011-06-06
If doing this the the ftp way is not possible ......

I guess I will share  /var/cache/apt/archives/ using NFS mount it on my 2nd PC & copy the files.

Next, I will try to automate the process. 

APTONCD is too hectic for daily use. 

Thanks.

---

### Post by lkraemer on 2011-06-06
I'm assuming you are going to make your transfers over your Local Area
Network (LAN), and not over the WAN (Internet).  And that all Computers
are connected to your LAN via Wifi or Patch Cables to Router.....

All you need to do is install vsftp or ProFTP (Server) on the machine of
your choice.  Then install Filezilla (Client) on the remaining ones that
will be making the transfers.  Since you are Local (I'd suggest closing all
your OPEN Router ports for the time you will be making the ftp transfers)
you can just FTP the files to where you want them.  If your Router ports
are Open, then use DSA Key Authentication with SFTP to make sure your
connection is SECURE.  Or just setup and use FTPS or FTPES,
versus just FTP.

You will need to set the vsftp.conf or proftpd.conf file properly, but a
quick Google search will help you find some samples.

When you are finished I'd remove the FTP Server if you aren't using it as the
Port will be open on the Server Machine, and if the associated Router Port is
Open, you will be Probed/Attacked.  Check your LOG Files!!!!!
Another thing you can do is make sure on each powerup that the FTP
Server is STOPPED, if you don't want to uninstall it.........

While I haven't searched this forum for a HOWTO: on vsftp, you may want to start there.

NFS is probably the easiest and quickest, but once again keep in mind
what Router ports are Open during your transfers.

LK

---

### Post by linuxyogi on 2011-06-06
> **lkraemer said:**
> I'm assuming you are going to make your transfers over your Local Area
Network (LAN), and not over the WAN (Internet).  And that all Computers
are connected to your LAN via Wifi or Patch Cables to Router.....

All you need to do is install vsftp or ProFTP (Server) on the machine of
your choice.  Then install Filezilla (Client) on the remaining ones that
will be making the transfers.  Since you are Local (I'd suggest closing all
your OPEN Router ports for the time you will be making the ftp transfers)
you can just FTP the files to where you want them.  If your Router ports
are Open, then use DSA Key Authentication with SFTP to make sure your
connection is SECURE.  Or just setup and use FTPS or FTPES,
versus just FTP.

You will need to set the vsftp.conf or proftpd.conf file properly, but a
quick Google search will help you find some samples.

When you are finished I'd remove the FTP Server if you aren't using it as the
Port will be open on the Server Machine, and if the associated Router Port is
Open, you will be Probed/Attacked.  Check your LOG Files!!!!!
Another thing you can do is make sure on each powerup that the FTP
Server is STOPPED, if you don't want to uninstall it.........

While I haven't searched this forum for a HOWTO: on vsftp, you may want to start there.

NFS is probably the easiest and quickest, but once again keep in mind
what Router ports are Open during your transfers.

LK

I connect to the internet using an ADSL router with all its ports closed. I confirmed that at grc.com. So, I guess I can keep a port open **(on my Ubuntu box) **& run a service provided it is password protected.

This is what I want to do 

I want to remove all the existing repos from the sources.list and add an entry like this 

[ftp://192.168.1.10/local](ftp://192.168.1.10/local)

*local is the name of the shared folder on PC 1 ..... this is where all the packages are.

Or increase the priority of the local repo.

[FONT=Arial Narrow]*If go to go to **"Software Sources"** you will see ftp repos .... ftp://    *[/FONT]This is where I got the idea from.

Thanks.

---

