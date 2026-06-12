---
title: "Feisty Installation of Swat and Samba"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by rupert160 on 2007-07-23
I had a lot of trouble installing swat with samba and finally found a solution at:

[COLOR="Blue"][http://talkback.zdnet.com/5208-12354-0.html?forumID=1&threadID=32001&messageID=608553&start=118]("http://talkback.zdnet.com/5208-12354-0.html?forumID=1&threadID=32001&messageID=608553&start=118")[/COLOR]

i also added port = 901 to the /etc/xinetd.d/swat file to confirm port 901

hope this helps:

sudo apt-get install samba smbfs swat xinetd

Then I created a SAMBA user:

sudo smbpasswd -a username

Then edited/created the xinet config file:

sudo nano -w /etc/xinetd.d/swat

I put the following in it:

service swat
{
disable = no
socket_type = stream
protocol = tcp
user = root
wait = no
server = /usr/sbin/swat
}

Then I needed to restart xinet to use these settings:

sudo dpkg-reconfigure xinetd

Once all that was done, I could use SWAT to configure the SAMBA server by browsing to [http://127.0.0.1:901](http://127.0.0.1:901) on the Ubuntu machine.

---

### Post by LaurenceR on 2007-07-25
Following rupert160's installation worked perfectly for me first time except that when Samba opened it was in User mode and not Root so I do not appear to have access to Globals, Shares and Printers.

Any help to access as Root would be appreciated. I am using Dapper.

---

### Post by perspectoff on 2007-07-27
That did not work for me on Feisty.

I've gone back to editing smb.conf by hand.

---

