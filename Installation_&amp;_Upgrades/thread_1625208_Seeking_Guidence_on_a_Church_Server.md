---
title: "Seeking Guidence on a Church Server"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by pdohara on 2010-11-18
I am looking at my alternatives for a server for my church. We have a Staff of 8 that will be going up to 10 this year (we hope). At least one staff member works from home. Myself and another volunteer support the machines on the network. Here is what we currently have:
[LIST]
[*]A Network Attached Storage Device (Seagate BlackArmor 2TB, but Mirrored so only 1TB of space)
[*]2 MacBook Pros running Snow Leapord
[*]2 Dell Laptops (a couple of years old), one off site
[*]4 Dell Desktops (from about 4 years old to a couple of months old)
[*]A Sharp MX-4100N Multi-Function Printer (This is a copier, that can print also)
[/LIST]Why am I looking to add a server? I need some additional services. I am pretty happy with the NAS and the Sharp has a built in print server. I would like to add a local email server to cache our Web Host providers server. I am confident that I can do that with fetchmail, but am wondering if there is another alternative. I am looking at adding a WiFi Hot Spot to our building. I would need to setup the routing rules such that both the office and the WiFi users can access the Internet, but the WiFi users cannot access the office. My Switches support VLANs so I am thinking that I will put three NICs in the server and setup the routing rules accordingly. I don't know how to do this, but I am confident that it can be done.
The other services I am looking for I am less confident about. I would like the Ubuntu server to provide authentication. Currently, I have to maintain the users on each indivdual machine. I would rather have all the users on a single server. Obviously when the laptops are not on the office network they will still need to be able to login. My work laptop works this way, so I assume that the clients can be configured to do this. What I am not sure about is what do I need to setup on the Ubuntu server? 
The other service I am looking to setup is Internet Filtering. I believe this can be accomplished using Squidgaurd. again I do not know is there is another alternative. I am looking to filter pornography, gamlbing, anything else that will land my church in the local paper if I don't filter it. :D I understand that these filters are not 100%. Still it seems like I need to put a decent effort into it. Also, I am thinking I will filter both the office and WiFi networks.
Now that everything is secure, I would like the ability to VPN in to run remote desktop. As I said myself ando another voluteer support these machines. It would be noce to be able to "see" what is going on without having to go the the church. Furthermore I could show someone how to do something (like converting a video for PowerPoint), rather than droping by in the evening and doing it myself.
Final bit, I would like to have some sort of groupware application like Exchange. At least the ability to share calendars, ideally it would also host discussions, support a wiki, and other group activities.
 
Did I mention that this is all for a church? So the budget is pretty much my time. I can get a machine I am sure, but software and support costs need to be kept to a minimum. We can pay for things we have to, but money is always tight.
 
I am not necessarily looking for answers so mush as looking for links to documents that describe the options. 
 
Thanks for your time on this.
 
Pat O
IT Volunteer
[Woodridge Community Church]("http://woodridge.cc")

---

### Post by Old_Grey_Wolf on 2010-11-19
I wish I could be more specific in my replay; however, you have a long list of services you want. It may be easier to get more detailed responses if you divide it up into multiple posts with some additional detailed information.

> **pdohara said:**
> Here is what we currently have:
[LIST]
[*]A Network Attached Storage Device (Seagate BlackArmor 2TB, but Mirrored so only 1TB of space)
[*]2 MacBook Pros running Snow Leapord
[*]2 Dell Laptops (a couple of years old), one off site
[*]4 Dell Desktops (from about 4 years old to a couple of months old)
[*]A Sharp MX-4100N Multi-Function Printer (This is a copier, that can print also)
[/LIST]


Do the Dell computers run Microsoft Windows or Linux or both?

I can't suggest anything for the 2 MACs as I know nothing about them.

> **pdohara said:**
> I am looking at adding a WiFi Hot Spot to our building. I would need to setup the routing rules such that both the office and the WiFi users can access the Internet, but the WiFi users cannot access the office. My Switches support VLANs so I am thinking that I will put three NICs in the server and setup the routing rules accordingly. I don't know how to do this, but I am confident that it can be done.

If your switches support VLANs you should be able to get that working as you have already alluded to. It could be done with subnets and ACLs as well. That is all something specific to the switches you have. What vendor and model do you have?

> **pdohara said:**
> The other services I am looking for I am less confident about. I would like the Ubuntu server to provide authentication. Currently, I have to maintain the users on each indivdual machine. I would rather have all the users on a single server. Obviously when the laptops are not on the office network they will still need to be able to login. My work laptop works this way, so I assume that the clients can be configured to do this. What I am not sure about is what do I need to setup on the Ubuntu server? 

Linux uses LDAP for this. Here is a Wikipedia link [http://en.wikipedia.org/wiki/LDAP](http://en.wikipedia.org/wiki/LDAP). Microsoft Windows uses Active Directory. Here are a few articles about LDAP and Active Director authentication [http://www.mhsoftware.com/caldemo/manual/en/470.htm](http://www.mhsoftware.com/caldemo/manual/en/470.htm), [http://www.netid.washington.edu/documentation/ldapAuth.aspx](http://www.netid.washington.edu/documentation/ldapAuth.aspx).

You can use Google for more information. Integrating LDAP and Active Directory is **not** easy.

> **pdohara said:**
> Now that everything is secure, I would like the ability to VPN in to run remote desktop. As I said myself ando another voluteer support these machines. It would be noce to be able to "see" what is going on without having to go the the church. 

For VPN read this Ubuntu Wiki [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN). Of course you can Google for more information.

> **pdohara said:**
> Final bit, I would like to have some sort of groupware application like Exchange. At least the ability to share calendars, ideally it would also host discussions, support a wiki, and other group activities.

Use Google to search on "LAMP stack". Ubuntu has the components in the repositories. Here is an example of one method to get a LAMP stack on Ubuntu [http://theindexer.wordpress.com/2009/02/02/installing-a-lamp-stack-on-ubuntu-using-apt/](http://theindexer.wordpress.com/2009/02/02/installing-a-lamp-stack-on-ubuntu-using-apt/). 

If you want a Bulletin Board like the Forums then install something like mybb or phpbb (phpbb is in the Ubuntu repositories) on top of the LAMP stack. Google on this as well. There are several Wiki packages you can install. Here is an example [http://www.mediawiki.org/wiki/MediaWiki](http://www.mediawiki.org/wiki/MediaWiki). Once again Google for alternatives.

---

