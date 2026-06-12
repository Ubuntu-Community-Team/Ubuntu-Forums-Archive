---
title: "Ubuntu Small Business network"
date: 2021-11-11
forum: Installation &amp; Upgrades
---

### Post by greene-dog on 2021-11-11
I've been using Linux for about 20 years and have only dealt with servers and home desktop.

My current office is just a bunch of plan desktops with no user control.

What I'd like to find is if Ubuntu have an option of creating a Small Business network similar to the Microsoft Small Business network.

I'd like to have a server with all accounts in it and storage for user's data.  

Then each user will have an account and all desktop will be either Ubuntu or Windows and maybe Apple for users to log into and use.

Does this exist? 

If so, is there a "How to" manual so one could set up?

Thanks

---

### Post by grahammechanical on 2021-11-11
Please explain what "Microsoft Small Business network" is. I am a home user. I know that there are server editions of Ubuntu. You must know that as well. Are you inquiring about some kind of support service. If so, then the people to ask are called Canonical. They are the sponsors of Ubuntu and they offer all kinds of paid for service arrangements.

Perhaps you are thinking of a server version of Ubuntu that comes with certain default applications. Some enlightenment would help make this thread educational.

Regards

---

### Post by TheFu on 2021-11-11
There is no all-in-one answer from Canonical.  There are many reasons that having a single system for everything is a terrible idea for security. It is best to logically separate some network services onto different systems.

If you start with the 20.04 Server Guide ... help.ubuntu.com ... you'll see the different options.  But as the administrator, YOU are expected to understand the security issues and setup a secure network for each service, adding mitigations for those things that apply to your network.  All our networks are a little different and we each have different risks, so the 1-size-fits everyone that some other OS vendors sell doesn't make sense.

For centralized user management, I'd use LDAP (of some sort). There are multiple tools for this - all are F/LOSS. LDAP has been used in the Unix world for about 25 yrs. Some networks use NIS+. Nobody should use NIS due to security flaws. Whether Kerberos is needed or not is a different question.

For centralized user HOME directories, I'd use NFS with autofs.  This is a well-known and understood solution. It has been in the Unix world for 30+ yrs. Whether Kerberos is needed or not is a different question.  Also, last time I checked, Canonical's snap packages failed to work with NFS as it is typically used, so that could be a huge consideration.

For maintaining systems, any devops tool can be used. Or you can create your own scripts like admins have been doing for 40+ yrs - before some marketing person came up with "devops".  I have a mix of Ansible and my own scripts.

For centralized system management, you'll want DNS and DHCP. I run these on different systems for security reasons. Also, any system that isn't portable has a static IP configured ON-THE-SYSTEM.

Print servers ... that's something CUPS has been doing for decades.  On a Linux-only network, no need for samba, especially when you have faster, more flexible, native, NFS.

There are a bunch of other network services you might want inside a small company - perhaps a document server, project management server, CSM, and CRM server - all integrated together.  Which are needed depend on the business.  I also run email and nextcloud servers. The nextcloud server in my tiny company is used for video conferencing too. I've been tempted to setup a Google-Docs-like solution integrated into NextCloud too. Nextcloud is great for some things, but not so great for others.  For serious document management, I've been disappointed, but for notes, todo lists, video conf, and a few other things, it works really well.  I ran a VoIP server for a few years, but ended up deciding that outsourcing that cheaply was a better use of my time.  

These days, you probably want a full VPN server and perhaps remote desktops.  We typically had 5 concurrent users per 2G "desktop", but scaling isn't hard. Project teams can access NFS storage and work together on files.   Linux can handle all these ... but again, you don't want to put them onto the same system.

And don't forget a backup server.  If you use NFS and don't allow local storage to be used, then you don't need to backup nearly so much stuff on each desktop. They would have programs and system settings, but not data or user config files, which would be on NFS storage.

Each of these things will need resources and that resource growth will mean you'll probably want to add more hardware for specific needs.

I know nothing about Apple, but it is Unix-like, so NFS and LDAP should work.

If you are really new to administration, seek out a book for 20.04 that covers the things you need. Having a consistent source of information will usually prevent huge gaps in the solution.  And always remember that just because something works, that doesn't mean that it is secure.

There are a few small-biz all-in-one servers by others, but those have mostly died out from what I can tell. I think they attempted the 1-size fits everyone model and found that just isn't true.

When I setup our network, we didn't mandate any clients, just that they had to support standard protocols.  I didn't tackle any desktop management, since nearly all workers are remote. Also, most of our services cannot be accessed directly from the internet without using our VPN. That includes email and nextcloud. No VPN, no access.

---

