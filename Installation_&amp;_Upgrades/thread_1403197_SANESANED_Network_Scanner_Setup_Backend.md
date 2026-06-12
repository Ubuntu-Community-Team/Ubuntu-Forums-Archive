---
title: "SANE/SANED Network Scanner Setup Backend"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by swingboy3 on 2010-02-10
Remotely accessing your scanner is a pretty cool feature for your Ubuntu Server setup.  It is pretty handy to have one scanner that everyone can use and you don't have to unplug a scanner find drivers for it and hope that the scanning software works.  You may have found out that it is handy to have a network printer, this should help you to get your network scanner running.

_________________________________________________________________



#1  My Setup

I am running Ubuntu 9.10 Karmic Koala. My scanner is actually a printer/scanner/copy combo HP F4280.  I have the printer already on a samba network share.  


_________________________________________________________________

#2  Get your scanner working

First of all make sure that your scanner is working on the local machine.  Plug it in and  see if it automagically installs. If XSANE is not installed install it from either the Synaptic Package Manager or by doing:
> sudo apt-get install xsane
Open up xsane and make sure you can scan something.  If you have troubles you'll need to consult other sources.

_________________________________________________________________

#3  Install Necessary software

The first thing extra to install is xinetd.  Once again do this either through synaptic package manager or by:
> sudo apt-get install xinetd
This should create a config file at /etc/xinetd.conf
You need to edit this.  Open a command window and type
> sudo cp /etc/xinetd.conf /etc/xinetd.conf.old
sudo nano /etc/xinetd.conf
I changed a little bit of the file so that now it looks like this
> # log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d

service sane-port
{
  socket_type = stream
  server = /usr/sbin/saned
  protocol = tcp
  user = root
  group = saned
  wait = no
  disable = no
}


Now we need to install the Sane Backend.  The backend is the part that allows other frontends to connect remotely.

I downloaded the backend from the sane website [http://www.sane-project.org/]("http://www.sane-project.org/")
This downloads a tar.gz file which you need to open, compile and make as follows.

> tar xvf  sane-backends-1.0.20.tar.gz
cd  sane-backends-1.0.20
sudo ./configure
sudo make
sudo make install

Now we need to let network devices have access to this device.  This is done by editing the config file in the folder /etc/sane.d/ by the following

> sudo nano /etc/sane.d/saned.conf

This file should be pretty much empty. Past in something like this

> localhost
192.168.1.0/24


This little bit of code allows these network devices to have access to your scanner.  The first line allows a local scanner, and the second line allows everything on the 192.168.1.xx network.  If you want you can allow this to specific ip addresses.

_________________________________________________________________

#4  Access it remotely

Of course the beauty of this is that you can access this from a windows machine, or a linux machine.  Maybe you can from a MAC but that is a bad word in my house.

The windows client/frontend can be found [here]("http://sanetwain.ozuzo.net/")
The Linux version can be found [here]("http://alioth.debian.org/frs/?group_id=30186")

I regret to report that I have only used the windows frontend.  It is very easy to setup, it just requires the ip address of the backend and permissions.


_________________________________________________________________

I'm by no means an expert at this.  In fact my Linux guru buddy MG helped me with this the most and got most of it working.  I just wanted to pass this on.  Feel free to ask questions but I hope others can answer them better than myself

---

