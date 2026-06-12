---
title: "Why my ubuntu net boot installation can not recognize local repository?"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by suim on 2007-07-19
Hi all,

I am a newbie in Ubuntu. I am trying to do Ubuntu auto installation in local Network. It can auto boot with PXE NIC and begin to initial the installation. But installation program can not get packages source from local repository. It always reports 
"Bad archive mirror
The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror
" 

With "ps -a" in the console, I can find installation program always try to do : 
wget -q [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) ...

I suspect it is because it can not recognize kernel parameter: url=http://192.168.1.1/tftpboot/ubuntu.cfg , because  ubuntu.cfg already provides a local server destination (192.168.1.2). 
 
I did following:
1. I have get a Feisty desktop CD and Feisty netboot packages.
2. I have setup DHCP server, tftp server and HTTP server.
3. I have copied Feisty CD contents to local [http://192.168.1.2//install/i386/ubuntu/ubuntu7-4](http://192.168.1.2//install/i386/ubuntu/ubuntu7-4)
4. I have copied netboot packages(kernel, intird, pxe etc.) to 192.168.1.1:/tftpboot/
5. I made a simple preseed config file ubuntu.cfg.

The ubuntu.cfg is like:
-------------------
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
d-i     archive-copier/desktop-task     string ubuntu-standard
d-i     archive-copier/ship-task        string
d-i     pkgsel/install-pattern  string ~t^ubuntu-standard$
d-i     pkgsel/language-pack-patterns   string
d-i     netcfg/choose_interface select auto
d-i     netcfg/get_hostname     string unassigned-firewall
d-i     netcfg/get_domain       string unassigned-domain
d-i     netcfg/wireless_wep     string d-i     mirror/http/hostname    string 192.168.1.2
d-i     mirror/http/directory   string /install/i386/ubuntu/ubuntu7-4
d-i     mirror/http/proxy       string
-------------------

The PXE boot cfg file is like:
-------------------
DEFAULT install
timeout 5

LABEL install
    kernel installer/i386/ubuntu/ubuntu7-4/linux
    append vga=normal auto url=http://192.168.1.1/tftpboot/ubuntu.cfg auto=true priority=critical locale=en_NZ kbd-chooser/method=us interface=auto locale=en_US console-setup/ask_detect=false console-setup/layoutcode=us initrd=installer/i386/ubuntu/ubuntu7-4/initrd.gz -- 
--------------------

I have read a lot of documents, but still could resolve it. 
Could anybody give a hand?  Thank you so much.

Best Regards,
Suim.

---

### Post by ubuntu.daemon on 2007-07-19
yay! lol i get to pass this on!  you probably didn't set up your dhcp.conf on your server end.....

what are you using for the domain-name-server?  post me  your file

---

### Post by suim on 2007-07-19
Hi,

Thanks for quickly reply. 
I think my DHCP is workable, as the target machine can do PXE booting up and get the IP address. The Ubuntu netboot kernel and initrid are working. 

And unfortunately, my internal network doesn't config DNS. All machines are just using IP address. And all internal machines can not bypass the firewall to get Internet information. Do you think it is the issue? But I already set up an internal file server to provide the resource. ;(

I was puzzled why the installation program would always try to get the mirrors info from [http://archive.ubuntu.com/](http://archive.ubuntu.com/)... And fail to go on. 
It looks strange.

---

### Post by aktelmiele on 2007-08-29
Hi

I also have this problem.

I am using tftp for windows

I get this error message, yet when I run ipconfig, I have a correct IP address and when I can successully run the wget command to retrieve google home page

I have tried numerous different archives yet I keep getting the same error

Does anybody have any ideas as to what I am doing wrong or what the issue is?

Thanks

---

### Post by skmah on 2007-10-01
I'm having similar difficulties. I have a network boot CD which reads a preseed file from our local web server. I extracted the contents of the Feisty 7.04 DVD on the web server and pointed the ubuntu repository to it.

It's complaining about the following:

The specified Ubuntu archive mirror is either not available, or does not have a  valid Release file on it. Pleas try a different mirror.

I even pointed it to a local apt-mirror that my coworker set up.

---

### Post by skmah on 2007-10-02
OK, I have something working now.

I have the boot CD load the preseed.cfg from a url. That preseed file points to a url I extracted from the DVD. It partition fine, installs ubuntu-desktop but fails at the security.ubuntu.com updating part.

I didn't put in a proxy server, because I want it to point to a local mirror of archive.ubuntu.com.

d-i     apt-setup/uri_type      select http
d-i     apt-setup/hostname      string mylocalserver.domain.com
d-i     apt-setup/directory     string /ubuntu/
d-i     apt-setup/another       boolean false
d-i     apt-setup/security-updates      boolean true

I also tried apt-setup/local0/repository, but not sure what the syntax is

---

