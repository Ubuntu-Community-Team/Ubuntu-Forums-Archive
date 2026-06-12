---
title: "Setting Up Squid Proxy server (simple proxy server)."
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by lpwaqas on 2011-09-06
Hello,

I was in a need to setup squid proxy server; (for private web browsing from public places ;)) and I got stuck with the new version of the squid avialable with Ubuntu Server which is squid 2.6 believe me its configuration file ($nano /etc/squid/squid.conf, you can use nano or vi to edit this file) is a mess as always :D

ALL you need an Linux server / VPS with Ubuntu (CentOS, RHEL, Fedora, FreeBSD) server connected to the internet all the time (usually a web-server at your host or at your ISP) and you can use it for the proxy server so whenever and wherever you are your internet traffic goes through it and no one knows what are you browsing its also known for its caching (super fast browsing).:popcorn:

To install just type in:

ubuntu:
#apt-get install squid
#aptitude install squid
Other distros:
#yum install squid


So here are the few changes you need to make for the installation of the squid server;

1. first of all comment the following; [because this line waisted my two hours everything was setup but I was unable to browse simple http pages and then a Linux Guru saved me by pointing this argument.]
# Deny CONNECT to other than SSL ports #http_access deny CONNECT !SSL_ports2. What port you would be using for the squid server; by-default its set to 3128 so change the following
# Squid normally listens to port 3128 http_port 3128

3. ACL's aaaaw its a mess :) so if you access it from one country you can use the following settings like I did;
acl our_networks src 111.111.0.0/16 222.222.0.0/16 333.333.0.0/16 http_access allow our_networks 
[Just to make it simple, just goto [www.whatismyip.com]("http://www.whatismyip.com") and then copy first two sub-nets replace the second and third
with the zero's and then added it if you are using multiple ISP's just repeat the process you can add as many as you 
want to]

4. What purpose you be using this proxy for for example if you need to access a site that works with the different port like 8080
or lets say you need to access Cpanel with port 2086 using this proxy server then you will have to add these ports to the following sections
#Recommended minimum configuration; BTW following are already there so just add per your requirements. acl all src 0.0.0.0/0.0.0.0 acl manager proto cache_object acl localhost src 127.0.0.1/255.255.255.255 acl to_localhost dst 127.0.0.0/8 acl SSL_ports port 443 acl Safe_ports port 80        # http acl Safe_ports port 21        # ftp acl Safe_ports port 443        # https acl Safe_ports port 70        # gopher acl Safe_ports port 210        # wais acl Safe_ports port 1025-65535    # unregistered ports acl Safe_ports port 280        # http-mgmt acl Safe_ports port 488        # gss-http acl Safe_ports port 591        # filemaker acl Safe_ports port 777        # multiling http
acl Safe_ports port 2986         #MINE :p

5. Make sure that deny all is hashed out (commented) otherwise squid wont start.
http_access allow localhost #http_access deny allNo save the squid.conf file and start the squid server using;
service squid start if it doesnt start (it fails) it means that you missed some of the settings just go over the 5 points given above again.

After that you will have to configure your web-browser i.e. , Firefox to use that proxy server; just follow the instructions below

Firefox connection settings:

If you connect to the Internet through a proxy server that is having connection problems, you will not be able to load websites. To check your Firefox proxy settings:

    At the top of the Firefox window, click on the Edit menu and select Preferences. (OR Tools > Settings)
    Select the Advanced panel.
    Select the Network tab.
    In the Connection section, click Settings....
    Change your proxy settings:
Enter the IP of your Server Enter the port and check all options and click on save and you are ready to go.
        If you don't connect to the Internet through a proxy (or don't know whether you connect through a proxy), select No Proxy.
    Close the Connection Settings window.
    Click Close to close the Preferences window. 

Have a nice Play :) with squid.

---

### Post by hth0923 on 2012-01-17
Hi 

Many thanks for the guide, I did follow it and everything has been set up, it works great within my local network, but it is not working at all for the remote computers. could you please point them out for me?

1, How to enable remote host access?
2, How to enable username and password to protect the proxy server being used by other people?

Many thanks.
hth0923

---

