---
title: "Fiesty Root? and other dumb questions"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by quonsar on 2007-04-22
Why does Fiesty have a root user? Previously I used Dapper and it had no root user. Is the root users password the same as mine (first installed user)? Is there some reason for this change I should be aware of?

How can I make the Users & Groups applet display all users and groups? Its help file says this is dependent on setting /apps/gnome-system-tools/users in gconf editor to show all. I have done this to no avail. The Users app still shows only myself and root as users, and is hiding many groups as well. This is highly annoying behavior!

Previously on Dapper I had Apache2/PHP using mod_auth_pam without a problem. Now its not working. I found a thread that said I had to add the user www-data to the shadow group (neither of which are visible in the users-admin applet, see above!) but i was able to do that from the command line. The same thread said I needed to create a link /etc/pam.d/httpd pointing to /etc/pam.d/apache2, which i also did. no go so far, apache2 error log says "Internal error: pcfg_openfile() called with NULL filename" and the virtual host error log says "Bad file descriptor: Could not open password file: (null)".  :confused: ](*,) 

Anyone? Beuller?  :)

---

### Post by tehbizz on 2007-04-22
Dapper had a root user but you had to `sudo passwd root && sudo su` to login as root.  I'm pretty sure this was explained on the forums back when Dapper came out and it's probably still on help.ubuntu.com or wiki.ubuntu.com somewhere.

---

### Post by quonsar on 2007-04-22
yes, i should have been clearer - why does fiesty have an easily accessible, blatantly visible root user, and what is the reason for this change?

:popcorn:

---

### Post by quonsar on 2007-04-22
*thud*

---

