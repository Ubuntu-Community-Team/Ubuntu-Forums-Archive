---
title: "What do I need to do??"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by macmike on 2010-05-11
What I need from someone, customized to my needs, is a list of do this with these commands, make these directories and etc. Here is what I am trying to do:


I want to Virtual Name host three sites as follows through my one IP address:
1. [www.wilmingtoncoc.com](www.wilmingtoncoc.com) - Host as a WordPress site. Use Word press to put content on it.
2. [www.mikealrhughes.com](www.mikealrhughes.com) - Host by putting files up using some kind of ftp server by way of Dreamweaver.
3. [www.biblematters.net](www.biblematters.net) - a Mailman mailing list of my closed mailing list.

Right now my [www.wilmingtoncoc.com](www.wilmingtoncoc.com) is forwarded to my public IP address. I don't know if that is the way it needs to remain or not. Someone can tell me that. Also I want to install Webmin to control all of this. Especially if I want to add another site to the mix in the future. I am trying to do all of this with Ubuntu 10.04. Also need to know what I will need to do DNS wise to make it work. I went to Dyndns.com and couldn't make heads or tails to what I needed from them.  Any help by anyone appreciated.

Thanks,

Mike Hughes

---

### Post by lechien73 on 2010-05-11
Hi Mike,

That's quite a list :) I don't think I'll be able to help you with all of it, but perhaps some of this might point you in the right direction.

With regard to virtual hosting on Ubuntu, everything you've asked is certainly possible. You need to install apache2, so:

```
sudo apt-get install apache2
```

When that's installed, open a web browser and go to: [http://localhost](http://localhost) and you should see a test page.

To configure virtual hosting in Apache, edit the /etc/apache2/apache2.conf file and add the following line to the end:

```
NameVirtualHost address:port
```

Replace "address" with your public IP address (see below) and port would normally be port 80.

In the /etc/apache2/sites-available directory, create a file for each of the virtual domains you're serving, e.g.: wilmingtoncoc.com

In the file, put the following:

```
<VirtualHost address:port>
ServerName wilmingtoncoc.com
ServerAlias www.wilmingtoncoc.com
ServerAdmin your-email-address
DocumentRoot /var/www/wilmingtoncoc.com/html
</VirtualHost>

```
Again, in the <VirtualHost...> tag, replace "address" with your public IP address and "port" with, probably, 80. Create the same files for the other sites you're hosting.

Now, type the following:

```
cd /etc/apache2/sites-enabled
ln -s ../sites-available/wilmingtoncoc.com
sudo service apache2 restart

```
Apache is now configured for virtual hosting of your sites, and they're available and enabled. You'll have to check Wordpress for details of how to set up their self-hosted solution, but the content of your sites needs to go in the /var/www/[sitename]/html folder, where [sitename] is, for example, wilmingtoncoc.com

If you're hosting the sites in-house then, ideally, you should have a static IP address for your Internet connection. You then need to ask the providers hosting your domain names to point them to that IP address. You may also need to configure your router to allow port 80 to forward to the internal IP address of your Ubuntu box.

This is a short intro, but I hope it sets you off in the right direction.

---

### Post by macmike on 2010-05-11
Matt:

I appreciate it that is a start. I have my ISP through Comcast they don't do static IP's. I understand I might have to do some with a DNS service because of that. If I can get the Wilmingtoncoc site up that will be an accomplishment. I tried the local host thing all I get is it works. I don't see a /etc/apache2/sites-available directory. I typed that in and it acted like it wanted to create a file named sites-available directory.
I did cd /etc/apache2/sites-enabled
ln -s ../sites-available/wilmingtoncoc.com
I got an access denied.
Then did sudo service apache2 restart

Came back and said NameVirtualHost *:80 has no VirtualHosts


Mike Hughes

---

### Post by lechien73 on 2010-05-11
Hi Mike,

Glad the initial install works. You'll have to transfer your domain name to a service like DynDNS. So select their Managed DNS and Domain Name service.

On your Ubuntu box, you'll need to use a client, which will dynamically update their servers with your IP address: [http://www.dyndns.com/support/clients/#linux](http://www.dyndns.com/support/clients/#linux)

I've never used or set-up DynDNS, so I can't vouch for their service, but you're probably looking at 24-48 hours to change your DNS record and get it to propagate.

---

### Post by macmike on 2010-05-11
I am still getting this message - Came back and said NameVirtualHost *:80 has no VirtualHosts

---

### Post by lechien73 on 2010-05-11
Have you created a file named wilmingtoncoc.com in the /etc/apache2/sites-available directory, as per the instructions in my original post and the details in the PM I sent you?

You can use <VirtualHost *:80> in these files as well.

---

