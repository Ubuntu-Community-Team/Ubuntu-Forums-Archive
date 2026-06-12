---
title: "100% Works Ubuntu 12.04 LTS + Freeradius + Coova-Chill + daloRADIUS"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by laughmo on 2012-10-12
**[FONT=&amp]100% Works Ubuntu 12.04 LTS + Freeradius + Coova-Chill + daloRADIUS[/FONT]**
  
  **[FONT=&amp]Pre-requisites[/FONT]**
  [FONT=&amp]-Ubuntu 12.04 LTS[/FONT]
  [FONT=&amp]-2 NICs eth0 connected to Internet on either static or dhcp, eth1 connect to clients with no IP address[/FONT]
  
  **[FONT=&amp]Install Ubuntu 12.04 LTS Server[/FONT]**
  [FONT=&amp]- Install LAMP, SSH Server[/FONT], BIND
  
  [FONT=&amp]Update packages cache[/FONT]
  [FONT=&amp]    3  sudo apt-get update[/FONT]
  
  **[FONT=&amp]Install freeradius[/FONT]**
  [FONT=&amp]   12  sudo apt-get install freeradius freeradius-mysql apache2 php5 libapache2-mod-php5 mysql-server mysql-client php5-mysql[/FONT]
  
  [FONT=&amp]Setup FQDN[/FONT]
  [FONT=&amp]   13  nano /etc/apache2/httpd.conf [/FONT]
  [FONT=&amp]      e.g.[/FONT]
  [FONT=&amp]      servername ppPortal.local[/FONT]
  
  [FONT=&amp]Download daloradius-0.9-9[/FONT]
  [FONT=&amp]   15  wget [http://sourceforge.net/settings/mirror_choices?projectname=daloradius&filename=daloradius/daloradius0.9-9/daloradius-0.9-9.tar.gz](http://sourceforge.net/settings/mirror_choices?projectname=daloradius&filename=daloradius/daloradius0.9-9/daloradius-0.9-9.tar.gz) [/FONT]
  
  [FONT=&amp]   17  tar zxvf daloradius-0.9-9-rc1.tar.gz -C /var/www/[/FONT]
  [FONT=&amp]   18  sudo tar zxvf daloradius-0.9-9-rc1.tar.gz -C /var/www/[/FONT]
  [FONT=&amp]   21  cd /var/www/[/FONT]
  [FONT=&amp]   23  sudo mv daloradius-0.9-9 daloradius[/FONT]
  [FONT=&amp]   26  cd daloradius/contrib/db/[/FONT]
  
  **[FONT=&amp]Create RADIUSDB database[/FONT]**
  [FONT=&amp]   32  mysql -u root -p[/FONT]
  [FONT=&amp]mysql> create database radiusdb;[/FONT]
  [FONT=&amp]mysql>quit[/FONT]
  [FONT=&amp]   35  mysql -u root -p radiusdb < fr2-mysql-daloradius-and-freeradius.sql [/FONT]
  [FONT=&amp]   36  mysql -u root -p[/FONT]
  [FONT=&amp]mysql>CREATE USER 'raddbuser'@'localhost';[/FONT]
  [FONT=&amp]mysql>SET PASSWORD FOR 'raddbuser'@'localhost' = PASSWORD('raddbpass');[/FONT]
  [FONT=&amp]mysql>GRANT ALL ON radiusdb.* to 'raddbuser'@'localhost';[/FONT]
  [FONT=&amp]mysql> quit[/FONT]
  
  **[FONT=&amp]Test Freeradius[/FONT]**
  [FONT=&amp][[https://help.ubuntu.com/community/WifiDocs/CoovaChilli?highlight=%28ManufacturerModel%29]](https://help.ubuntu.com/community/WifiDocs/CoovaChilli?highlight=%28ManufacturerModel%29])[/FONT]
  
  [FONT=&amp]The default FreeRadius setup authorize's usernames and passwords from a "file" found in /etc/freeradius/users. We should test the default FreeRadius setup before we change the authorization link from "file" to "sql" (mysql).[/FONT]
  
  [FONT=&amp]Add username an password to our user "file". edit "John Doe"[/FONT]
  
  [FONT=&amp]nano -w /etc/freeradius/users[/FONT]
  
  [FONT=&amp]NOTE: you have to work as root to see this file[/FONT]
  
  [FONT=&amp]uncomment[/FONT]
  
  [FONT=&amp]"John Doe"     Auth-Type := Local, User-Password == "hello"[/FONT]
  [FONT=&amp]               Reply-Message = "Hello, %u"[/FONT]
  
  [FONT=&amp]At this point you need to reboot your ubuntu box[/FONT]
  
  [FONT=&amp]reboot[/FONT]
  
  [FONT=&amp]Check FreeRadius config files.[/FONT]
  
  [FONT=&amp]sudo /etc/init.d/freeradius stop[/FONT]
  [FONT=&amp]sudo freeradius -XXX[/FONT]
  
  [FONT=&amp]If all goes well the last line should display[/FONT]
  
  [FONT=&amp]Mon Jun 29 15:24:34 2009 : Debug: Ready to process requests.[/FONT]
  [FONT=&amp]Ctrl+C to exit.[/FONT]
  
  [FONT=&amp]NOTE: If you get error &#8220;Error binding to port for 0.0.0.0 port 1812&#8221;, it means freeradius is already running. Stop it by doing the following:[/FONT]
  
  [FONT=&amp]# ps &#8211;A | grep freeradius[/FONT]
  
  [FONT=&amp]To get process ID of freeradius[/FONT]
  [FONT=&amp]#kill -9 freeradius-PID[/FONT]
  
  [FONT=&amp]Start FreeRadius again[/FONT]
  
  [FONT=&amp]sudo /etc/init.d/freeradius start[/FONT]
  
  **[FONT=&amp]Test password authorization to "file"[/FONT]**
  
  [FONT=&amp]sudo radtest "John Doe" hello 127.0.0.1 0 testing123[/FONT]
  
  [FONT=&amp]If all goes well you should get a reply[/FONT]
  
  [FONT=&amp]Sending Access-Request of id 136 to 127.0.0.1 port 1812[/FONT]
  [FONT=&amp]        User-Name = "John Doe"[/FONT]
  [FONT=&amp]        User-Password = "hello"[/FONT]
  [FONT=&amp]        NAS-IP-Address = 255.255.255.255[/FONT]
  [FONT=&amp]        NAS-Port = 0[/FONT]
  [FONT=&amp]rad_recv: Access-Accept packet from host 127.0.0.1:1812, id=136, length=37[/FONT]
  [FONT=&amp]        Reply-Message = "Hello, John Doe"[/FONT]
  
[FONT=&amp]**Change authorization to sql**
[/FONT][FONT=&amp]change authorization to sql[/FONT]
  
  [FONT=&amp]in[/FONT]
  
  [FONT=&amp]/etc/freeradius/radiusd.conf [/FONT]
  
  [FONT=&amp]on line 683 include the sql module: uncomment the line "$INCLUDE sql.conf" and " $INCLUDE sql/mysql/counter.conf" in "modules { ... }"[/FONT]
  
  [FONT=&amp]If the above tests worked we can now change authorization from "file" to "sql" in:[/FONT]
  
  [FONT=&amp]/etc/freeradius/sites-available/default[/FONT]
  
  [FONT=&amp]comment "files" (line 152) and uncomment sql on line 159 also uncomment sql on line 428 under the "session {... }" section and also in the accounting section on line 383[/FONT]
  
**Counters**
Edit radius.conf file

Around line 710 in the instantiate section make sure you have,

chillispot_max_bytes
noresetcounter

which are our counters which we define in the next section. Then in   /etc/freeradius/sites-available/default, in the authorize section after  it has  the "Look in an SQL database..." it has an "sql" entry that may  be  commented out so uncomment it and add the new counters so that it is   now,

sql
chillispot_max_bytes
noresetcounter

That should be it. Now update the counter.conf in the next section.

**FreeRadius SQL counter.conf settings needed**
To match the radcheck and radgroupchecks we use then you also need to   add two matching counter.conf checks as follows. Edit the   /etc/freeradius/sql/mysql/counter.conf file (unless the counter is  already  defined in that), add the following at the end,

sqlcounter noresetcounter {
counter-name = Session-Timeout
check-name = Session-Timeout
reply-name = Session-Timeout
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
}

sqlcounter chillispot_max_bytes {
counter-name = ChilliSpot-Max-Total-Octets
check-name = ChilliSpot-Max-Total-Octets
reply-name = ChilliSpot-Max-Total-Octets
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
}
  
  **[FONT=&amp]Daloradius Web Interface Pre-requisites[/FONT]**
  [FONT=&amp]   36  apt-get install php-pear php5-gd php-db[/FONT]
  
  [FONT=&amp]# wget pear.php.net/go-pear.phar[/FONT]
  [FONT=&amp]# php go-pear.phar[/FONT]
  [FONT=&amp]# pear install DB[/FONT]
  
  [FONT=&amp]Test apache configuration[/FONT]
  [FONT=&amp]   54  apachectl configtest[/FONT]
  
  [FONT=&amp]Restart apache[/FONT]
  [FONT=&amp]   57  apachectl restart[/FONT]
  
  **[FONT=&amp]Install Coova-Chilli[/FONT]**
  [FONT=&amp]  103  wget [http://coova-chilli.s3.amazonaws.com/coova-chilli-1.2.9.tar.gz](http://coova-chilli.s3.amazonaws.com/coova-chilli-1.2.9.tar.gz) [/FONT]
  [FONT=&amp]  104  apt-get install build-essential linux-headers-server libssl-dev[/FONT]
  [FONT=&amp]  105  tar zxvf coova-chilli-1.2.9.tar.gz [/FONT]
  [FONT=&amp]  106  ls[/FONT]
  [FONT=&amp]  107  cd coova-chilli-1.2.9/[/FONT]
  [FONT=&amp]  111  ./configure --prefix= --enable-miniportal --with-openssl[/FONT]
  [FONT=&amp]  112  make[/FONT]
  [FONT=&amp]  113  make install[/FONT]
  [FONT=&amp]  114  cd[/FONT]
  [FONT=&amp]  116  wget [http://dfn.dl.sourceforge.net/project/haserl/haserl-devel/haserl-0.9.29.tar.gz](http://dfn.dl.sourceforge.net/project/haserl/haserl-devel/haserl-0.9.29.tar.gz)[/FONT]
  [FONT=&amp]  118  tar zxvf haserl-0.9.29.tar.gz [/FONT]
  [FONT=&amp]  119  cd haserl-0.9.29/[/FONT]
  [FONT=&amp]  120  ls[/FONT]
  [FONT=&amp]  121  ./configure --prefix=[/FONT]
  [FONT=&amp]  122  make[/FONT]
  [FONT=&amp]  123  make install[/FONT]
  
  **[FONT=&amp]Create chilli user[/FONT]**
  [FONT=&amp]     Useradd chilli[/FONT]
  **[FONT=&amp]Set freeradius and Chilli to start at boot time[/FONT]**
  [FONT=&amp]  124  update-rc.d freeradius defaults[/FONT]
  [FONT=&amp]  125  update-rc.d chilli defaults[/FONT]
  
  [FONT=&amp]Also there is a problem at rebooting time. The workaround is to put the following in[/FONT]
  
  [FONT=&amp]  127  nano /etc/rc.local [/FONT]
  
  [FONT=&amp]/etc/init.d/freeradius restart[/FONT]
  [FONT=&amp]/etc/init.d/chilli restart[/FONT]
  [FONT=&amp]exit 0[/FONT]
  
  [FONT=&amp]  128  cp /etc/chilli/defaults /etc/chilli/config[/FONT]
  [FONT=&amp]  133  reboot[/FONT]
  
  **[FONT=&amp]Check Chilli and freeradius status[/FONT]**
  [FONT=&amp]  138  ps -A | grep freeradius[/FONT]
  [FONT=&amp]  140  ps -A | grep chilli[/FONT]
  
  **[FONT=&amp]IPtables[/FONT]**
  [FONT=&amp]The creators of CoovaChilli have predefined rules for iptables, but their script needs a little help before it works. CoovaChilli's iptables config is done in the /etc/chilli/up.sh script which runs after the tun interface is up, so that the exact tun interface is known.[/FONT]
  
  [FONT=&amp]/etc/chilli/up.sh calls /etc/chilli/ipup.sh, if it exists. By default, it does not. If you need to run your own commands after the main iptables configuration is done, create /etc/chilli/ipup.sh and populate it however you like, being sure to make it executable (chmod +x /etc/chilli/ipup.sh) when done.[/FONT]
  
  [FONT=&amp]create[/FONT]
  
  [FONT=&amp]/etc/chilli/ipup.sh[/FONT]
  
  [FONT=&amp]with the following content:[/FONT]
  
  [FONT=&amp]# force-add the final rule necessary to fix routing tables[/FONT]
  [FONT=&amp]iptables -I POSTROUTING -t nat -o $HS_WANIF -j MASQUERADE[/FONT]
  
  [FONT=&amp]  142  nano /etc/chilli/ipup.sh[/FONT]
  [FONT=&amp]  143  chmod +x /etc/chilli/ipup.sh [/FONT]
  
  **[FONT=&amp]Daloradius Database connection settings[/FONT]**
  [FONT=&amp]  151  nano /var/www/daloradius/library/daloradius.conf.php[/FONT]
  
  [FONT=&amp]&#8226; $configValues['CONFIG_DB_ENGINE'] = 'mysql';[/FONT]
  [FONT=&amp]&#8226; $configValues['CONFIG_DB_HOST'] = 'localhost';[/FONT]
  [FONT=&amp]&#8226; $configValues['CONFIG_DB_USER'] = 'raddbuser';[/FONT]
  [FONT=&amp]&#8226; $configValues['CONFIG_DB_PASS'] = 'raddbpass';[/FONT]
  [FONT=&amp]&#8226; $configValues['CONFIG_DB_NAME'] = 'radiusdb';[/FONT]
  
  [FONT=&amp]Touch daloradius log file.[/FONT]
  [FONT=&amp]&#8226; touch /var/log/daloradius.log[/FONT]
  
  **[FONT=&amp]daloRADIUS 0.9-9 &#8211; QUCIK START[/FONT]**
  Fire up Firefox (or any other borowser) and go to the URL http://<localhost or the managemet system's ip>/daloradius.

  Default Log in with the administrator for management:

      **username:** administrator
**    password:** radius


  **[FONT=&amp]Create Profiles &#8211; Time Based Profile[/FONT]**
  [FONT=&amp]Go to Management tab > Select Profiles > Create New Profiles >Add Profile Attributes[/FONT]
  [FONT=&amp]Type Profile Name, e.g. 60Mins[/FONT]
  
  **[FONT=&amp]Add attributes[/FONT]**
  **[FONT=&amp]Check Attributes[/FONT]**
  [FONT=&amp]Simultaneous-Use = 1[/FONT]
  [FONT=&amp]Max-All-Session = 3600[/FONT]
  [FONT=&amp][this is in seconds, for 60mins = 3600seconds][/FONT]
  [FONT=&amp]Session-Timeout = 3600[/FONT]
  **[FONT=&amp]Reply Attributes[/FONT]**
  [FONT=&amp]Session-Timeout = 3600[/FONT]
  [FONT=&amp]Idle-Timeout = 60[/FONT]
  [FONT=&amp]Acct-Interim-Interval = 120[/FONT]
  
  **[FONT=&amp]Billing Plans &#8211; Time Based[/FONT]**
  [FONT=&amp]Go to Billing Tab> Select Plans > New Plan[/FONT]
  [FONT=&amp]1. Enter Plan Information details from Plan Name to Plan Active[/FONT]
  [FONT=&amp]2. Enter Time Settings details[/FONT]
  [FONT=&amp]3. Select Profile from the drop-down[/FONT]
  
  **[FONT=&amp]Add Hotspot[/FONT]**
  [FONT=&amp]Go to Management Tab > Hotspots > Click New Hotspot[/FONT]
  [FONT=&amp]Enter Hotspot Name and MAC Address of interface connected to clients, Click Apply[/FONT]
  
  **[FONT=&amp]Add NAS[/FONT]**
  [FONT=&amp]Go to Management > Nas > Click New NAS[/FONT]
  [FONT=&amp]Enter NAS Info, IP, NAS secret (e.g. testing123), NAS type, Other and NAS shortname. Set NAS Ports to 3997, Click Apply[/FONT]
  
  **[FONT=&amp]Create Pre-paid Vouchers &#8211; Batch Users &#8211; Walk-In[/FONT]**
  [FONT=&amp]Go to Management > Batch Users > Click Batch Add Users[/FONT]
  [FONT=&amp]Enter Account Info, Batch Id/Name, e.g. 60Mins_12_11_12, a Batch Description, Select Hotspot.[/FONT]
  [FONT=&amp]I use Create Random Users, with default username/password length of 8, and set number of instances to create (number of vouchers).[/FONT]
  [FONT=&amp]Select Group, e.g. 60Mins for 1 hour vouchers, Group Priority 0 or 1 is fine and then the Plan name for 1 hour. Click Apply[/FONT]
  [FONT=&amp]You can print the vouchers/tickets.[/FONT]
  
  **[FONT=&amp]Create Member User Accounts[/FONT]**
  [FONT=&amp]Go to Management > Users > Click New User[/FONT]
  [FONT=&amp]Enter Account Info, username, password and select Group. You can also enter User Info First/Last names, email, etc. Click Apply[/FONT]
  
  **[FONT=&amp]Testing Login[/FONT]**
  [FONT=&amp]Using a client connected to the same interface as the eth1, open a web browser. You should get an IP in this range 10.1.0.X. Go to [www.google.com]("http://www.google.com"). You will be redirected to the Coova login page. Login in to the Hotspot using either a Batch User or a Member User[/FONT]

---

### Post by laughmo on 2012-11-02
Edit radius.conf file
To do this, edit /etc/freeradius/radiusd.conf and pretty much ignore  everything except around about line 640 in the modules section uncomment  or make sure that you have,

$INCLUDE sql.conf

and then further down make sure you have,

$INCLUDE sql/mysql/counter.conf

Then further around line 710 in the instantiate section make sure you have,

chillispot_max_bytes
noresetcounter


which are our counters which we define in the next section. Then in  /etc/freeradius/sites-available/default, in the authorize section after it has  the "Look in an SQL database..." it has an "sql" entry that may be  commented out so uncomment it and add the new counters so that it is  now,


sql
chillispot_max_bytes
noresetcounter

That should be it. Now update the counter.conf in the next section.

FreeRadius SQL counter.conf settings needed
To match the radcheck and radgroupchecks we use then you also need to  add two matching counter.conf checks as follows. Edit the  /etc/freeradius/sql/mysql/counter.conf file (unless the counter is already  defined in that), add the following at the end,

sqlcounter noresetcounter {
counter-name = Session-Timeout
check-name = Session-Timeout
reply-name = Session-Timeout
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
}

sqlcounter chillispot_max_bytes {
counter-name = ChilliSpot-Max-Total-Octets
check-name = ChilliSpot-Max-Total-Octets
reply-name = ChilliSpot-Max-Total-Octets
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
}

---

### Post by kentucky on 2012-11-16
Hi, just wondering if this can be be done on a webserver as a central authentication system?

---

### Post by laughmo on 2012-11-22
Yes it can be done. I have done it on a web server. what type of authentication would you want to use?

---

### Post by ryabchikov on 2012-11-23
Thank you for this man, it`s good job.

---

### Post by chaps2001999 on 2012-12-21
Hi,

I’m tearing my hair out. I’ve got coova installed and running on Ubuntu server 12.04 folowing [https://help.ubuntu.com/community/WifiDocs/CoovaChilli](https://help.ubuntu.com/community/WifiDocs/CoovaChilli) guide.

Currently everything works except for the self registration page for new users http:/10.0.1.1:3990/www/register.chi which asks for new user details, I was up until yesterday getting a blank page but I resolved that by changing the config file in etc/chilli/ directory to "self". However my problem now is the register button doesn’t do anything when I click it???

I’ve spent 2 days trying figuring out why. I can login using chillispot test account and can create an account under daloradius. Do you happen to know how I can fix this problem and why the register.chi page doesn't do anything, its important I get this working so I can allow new users to access the internet.,

Thanks 

Raj

---

### Post by Clifweb on 2013-01-18
I followed the instruction but when I got to daloradius web page I get the eth1 ip is none. when I connected a device directly to eth1 the laptop got the ip 10.1.0.2 but no internet and wasn't redirected to the login page. Can someone help figure out what I did wrong? or why it is not working.

---

### Post by laughmo on 2013-01-18
Clifweb, what interfaces do you have? eth0 is internet. could you share /etc/chilli/config file?

---

### Post by Clifweb on 2013-01-19
Here is my config.
eth0 connected to internet modem while the eth1 is connected currently for testing to the laptop but this will be connected to a wireless access point.

---

### Post by jeavonspablo on 2013-02-12
thanks a lot for this post. i followed the instructions and it works. i created some users and after trying to access the net, coovachilli redirected me to the login page. and the authentication really works.

im gonna to try this in a real network implementation at school.

---

### Post by jeavonspablo on 2013-02-12
> **laughmo said:**
> Edit radius.conf file
To do this, edit /etc/freeradius/radiusd.conf and pretty much ignore  everything except around about line 640 in the modules section uncomment  or make sure that you have,

$INCLUDE sql.conf

and then further down make sure you have,

$INCLUDE sql/mysql/counter.conf

Then further around line 710 in the instantiate section make sure you have,

chillispot_max_bytes
noresetcounter


which are our counters which we define in the next section. Then in  /etc/freeradius/sites-available/default, in the authorize section after it has  the "Look in an SQL database..." it has an "sql" entry that may be  commented out so uncomment it and add the new counters so that it is  now,


sql
chillispot_max_bytes
noresetcounter

That should be it. Now update the counter.conf in the next section.

FreeRadius SQL counter.conf settings needed
To match the radcheck and radgroupchecks we use then you also need to  add two matching counter.conf checks as follows. Edit the  /etc/freeradius/sql/mysql/counter.conf file (unless the counter is already  defined in that), add the following at the end,

sqlcounter noresetcounter {
counter-name = Session-Timeout
check-name = Session-Timeout
reply-name = Session-Timeout
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
}

sqlcounter chillispot_max_bytes {
counter-name = ChilliSpot-Max-Total-Octets
check-name = ChilliSpot-Max-Total-Octets
reply-name = ChilliSpot-Max-Total-Octets
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
}

i encountered a problem after following the above instructions. 
i can no longer start freeradius.

root@cportal:/etc/freeradius# /etc/init.d/freeradius restart
 * Stopping FreeRADIUS daemon freeradius                                         
* /var/run/freeradius/freeradius.pid not found...                       [ OK ]
 * Starting FreeRADIUS daemon freeradius                              [fail]

please help me solove this.. thanks.

---

### Post by jeavonspablo on 2013-02-12
> **laughmo said:**
> Edit radius.conf file
To do this, edit /etc/freeradius/radiusd.conf and pretty much ignore  everything except around about line 640 in the modules section uncomment  or make sure that you have,

$INCLUDE sql.conf

and then further down make sure you have,

$INCLUDE sql/mysql/counter.conf

Then further around line 710 in the instantiate section make sure you have,

chillispot_max_bytes
noresetcounter


which are our counters which we define in the next section. Then in  /etc/freeradius/sites-available/default, in the authorize section after it has  the "Look in an SQL database..." it has an "sql" entry that may be  commented out so uncomment it and add the new counters so that it is  now,


sql
chillispot_max_bytes
noresetcounter

That should be it. Now update the counter.conf in the next section.

FreeRadius SQL counter.conf settings needed
To match the radcheck and radgroupchecks we use then you also need to  add two matching counter.conf checks as follows. Edit the  /etc/freeradius/sql/mysql/counter.conf file (unless the counter is already  defined in that), add the following at the end,

sqlcounter noresetcounter {
counter-name = Session-Timeout
check-name = Session-Timeout
reply-name = Session-Timeout
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
}

sqlcounter chillispot_max_bytes {
counter-name = ChilliSpot-Max-Total-Octets
check-name = ChilliSpot-Max-Total-Octets
reply-name = ChilliSpot-Max-Total-Octets
sqlmod-inst = sql
key = User-Name
reset = never
query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
}

i encountered a problem after following the above instructions. 
i can no longer start freeradius.

root@cportal:/etc/freeradius# /etc/init.d/freeradius restart
 * Stopping FreeRADIUS daemon freeradius                                         
* /var/run/freeradius/freeradius.pid not found...                       [ OK ]
 * Starting FreeRADIUS daemon freeradius                              [fail]

please help me solve this.. thanks.

---

### Post by laughmo on 2013-02-12
eth0 is your internet interface. you have to set it either on dhcp or static ip

---

### Post by laughmo on 2013-02-12
can you start freeradius in debug mode
#freeradius -X

and paste the output you get. there is a line which will point out the error

---

### Post by jeavonspablo on 2013-02-12
> **laughmo said:**
> can you start freeradius in debug mode
#freeradius -X

and paste the output you get. there is a line which will point out the error


thanks for the response.. 

after issuing the command #freeradius -X it indicated that there are too many closing brackets in my counter.conf file.. 

i deleted the excess bracket at the end of the file and was able to start freeradius again..
thanks a lot..

---

### Post by laughmo on 2013-02-13
nice one!

---

### Post by jeavonspablo on 2013-02-13
good day!

do you in any way have a manual for configuring the daloradius web manager? 

can we add users that can also administer daloradius say for example adding vouchers and viewing bills and  accounts but not necessarily as powerful as an administrator? i'm referring to cashiers or managers. thanks for your help...

---

### Post by laughmo on 2013-02-14
i dont have a MANUAL but yes you can add admin daloradius users. when you login, go to Config>Operators>New operator
this will allow you to add admin users and set their permissions

---

### Post by jeavonspablo on 2013-02-14
thanks i tried it as soon as i read your post. vey helpful!

if i may, i'd like to ask more questions. thanks in advance.

i read these posts in the daloradius discussions:

[https://sourceforge.net/projects/daloradius/forums/forum/684102/topic/3311600](https://sourceforge.net/projects/daloradius/forums/forum/684102/topic/3311600) [https://sourceforge.net/projects/daloradius/forums/forum/684102/topic/3307738](https://sourceforge.net/projects/daloradius/forums/forum/684102/topic/3307738)


are these issues already solved with the last set of instructions in this thread?
id like to know because i really dont have an idea on what the last instructions do. im referring to those instructions wherein we set the sqlcounters in the counter file.. thanks

---

### Post by laughmo on 2013-02-15
yes the sql counters in my howto address all these and the user will be limited on either time or bandwidth.
there is however no documentation on these. i hope i can document this in another HOWTO

---

### Post by jeavonspablo on 2013-02-17
thanks ill be waiting for that.

---

### Post by jeavonspablo on 2013-02-18
good day.

i've got more questions. i hope you can help me. 

how do i enable the pop up that shows qfter authentication ? it would also indicate the elapsed time and remaining time of a user?

another thing is that im wondering if its possible for a user to be limited time based and packet based at the same time? e.g a user is given one day to access network resources but if he's already downloaded/uploaded a certain amount he can no longer access. thanks.

---

### Post by popoy35 on 2013-03-21
Hi good day!!!, I just want to build a server using this Ubuntu 12.04 LTS + Freeradius + Coova-Chilli, can you anyone help me to built from scratch....thank you

---

### Post by jeavonspablo on 2013-03-21
just follow the steps provided in this thread.

---

### Post by msmuneer on 2013-05-18
I am facing following error when i am trying to access daloradius, please help me in this regard.

**Database error**
		**Error Message: **DB Error: no such table
**Debug info: **SELECT  id, username FROM operators WHERE username = '' AND password = ''  [nativecode=1146 ** Table 'radiusdb.operators' doesn't exist]

---

### Post by 0651 on 2013-07-11
I've done step by step, dhcp is working, but the client can not login Coova.
can anybody help me?


thank you ...


I use Ubuntu 12 04 amd64

---

### Post by laughmo on 2013-07-12
hi,

do the following from the terminal window

$ /etc/init.d/freeradius stop
$ freeradius -XXX

then try to login

then paste the output of command freeradius -XXX here

---

### Post by rob-wieskamp on 2013-08-22
I noticed there is a dns problem when following the steps from this tutorial. Everything worked fine when typing in an ip address in the browser but typing the domain name didn't work (no redirection). So 74.125.136.138 works, but google.com not (time out error)

I changed the DNS server from opendns to HS_DNS1=10.1.0.1 and now everything works as it should.

---

### Post by ahmy2 on 2013-08-26
I have followed every step in your guide everything seems to be progressing ok but until i get to da point where i have 2 test Mr John Doe i`m getting this error 

 > root@test:~# sudo radtest "John Doe" hello 127.0.0.1 0 testing123
Sending Access-Request of id 130 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
rad_recv: Access-Reject packet from host 127.0.0.1 port 1812, id=130, length=20



Anyhelp apprciated

---

### Post by laughmo on 2013-08-26
have edit the /etc/freeradius/users file to uncommented the John Doe line?



> **jeavonspablo said:**
> thanks a lot for this post. i followed the instructions and it works. i created some users and after trying to access the net, coovachilli redirected me to the login page. and the authentication really works.

im gonna to try this in a real network implementation at school.

---

### Post by ahmy2 on 2013-08-26
> **laughmo said:**
> have edit the /etc/freeradius/users file to uncommented the John Doe line?


I have uncommented the line John Doe so the line is looking like this now  > John Doe     Auth-Type := Local, User-Password == "hello"
#         Reply-Message = "Hello, %u 


test results 

> root@test:/etc/freeradius#  sudo radtest "John Doe" hello 127.0.0.1 0 testing1Sending Access-Request of id 98 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
Sending Access-Request of id 98 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
Sending Access-Request of id 98 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
radclient: no response from server for ID 98 socket 3



---

### Post by laughmo on 2013-08-26
the line should be like this:

"John Doe"      Cleartext-Password := "hello"
                Reply-Message = "Hello, %{User-Name}"

when testing, run this command:

freeradius -XXX | tee testlog.log

post the contents of testlog.log here

---

### Post by ahmy2 on 2013-08-26
> **laughmo said:**
> the line should be like this:

"John Doe"      Cleartext-Password := "hello"
                Reply-Message = "Hello, %{User-Name}"

when testing, run this command:

freeradius -XXX | tee testlog.log

post the contents of testlog.log here



no sucess with testing John,  Here`s the result 


> root@test:/etc/freeradius#  freeradius -XXX | tee testlog.log
Mon Aug 26 15:01:09 2013 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Mon Aug 26 15:01:09 2013 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Mon Aug 26 15:01:09 2013 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Mon Aug 26 15:01:09 2013 : Info: PARTICULAR PURPOSE. 
Mon Aug 26 15:01:09 2013 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Mon Aug 26 15:01:09 2013 : Info: GNU General Public License v2. 
Mon Aug 26 15:01:09 2013 : Info: Starting - reading configuration files ...
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/radiusd.conf
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/proxy.conf
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/clients.conf
Mon Aug 26 15:01:09 2013 : Debug: including files in directory /etc/freeradius/modules/
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/expiration
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/detail
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/always
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/echo
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/unix
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/mschap
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/smsotp
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/sql_log
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/wimax
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/logintime
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/ippool
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/checkval
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/expr
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/perl
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/radutmp
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/krb5
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/files
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/cui
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/ldap
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/preprocess
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/pap
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/linelog
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/detail.log
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/pam
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/digest
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/exec
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/passwd
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/chap
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/policy
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/counter
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/etc_group
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/realm
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/modules/otp
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/eap.conf
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/policy.conf
Mon Aug 26 15:01:09 2013 : Debug: including files in directory /etc/freeradius/sites-enabled/
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Mon Aug 26 15:01:09 2013 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Mon Aug 26 15:01:09 2013 : Debug: main {
Mon Aug 26 15:01:09 2013 : Debug:     user = "freerad"
Mon Aug 26 15:01:09 2013 : Debug:     group = "freerad"
Mon Aug 26 15:01:09 2013 : Debug:     allow_core_dumps = no
Mon Aug 26 15:01:09 2013 : Debug: }
Mon Aug 26 15:01:09 2013 : Debug: including dictionary file /etc/freeradius/dictionary
Mon Aug 26 15:01:09 2013 : Debug: main {
Mon Aug 26 15:01:09 2013 : Debug:     prefix = "/usr"
Mon Aug 26 15:01:09 2013 : Debug:     localstatedir = "/var"
Mon Aug 26 15:01:09 2013 : Debug:     logdir = "/var/log/freeradius"
Mon Aug 26 15:01:09 2013 : Debug:     libdir = "/usr/lib/freeradius"
Mon Aug 26 15:01:09 2013 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Mon Aug 26 15:01:09 2013 : Debug:     hostname_lookups = no
Mon Aug 26 15:01:09 2013 : Debug:     max_request_time = 30
Mon Aug 26 15:01:09 2013 : Debug:     cleanup_delay = 5
Mon Aug 26 15:01:09 2013 : Debug:     max_requests = 1024
Mon Aug 26 15:01:09 2013 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Mon Aug 26 15:01:09 2013 : Debug:     checkrad = "/usr/sbin/checkrad"
Mon Aug 26 15:01:09 2013 : Debug:     debug_level = 0
Mon Aug 26 15:01:09 2013 : Debug:     proxy_requests = yes
Mon Aug 26 15:01:09 2013 : Debug:  log {
Mon Aug 26 15:01:09 2013 : Debug:     stripped_names = no
Mon Aug 26 15:01:09 2013 : Debug:     auth = no
Mon Aug 26 15:01:09 2013 : Debug:     auth_badpass = no
Mon Aug 26 15:01:09 2013 : Debug:     auth_goodpass = no
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug:  security {
Mon Aug 26 15:01:09 2013 : Debug:     max_attributes = 200
Mon Aug 26 15:01:09 2013 : Debug:     reject_delay = 1
Mon Aug 26 15:01:09 2013 : Debug:     status_server = yes
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug: }
Mon Aug 26 15:01:09 2013 : Debug: radiusd: #### Loading Realms and Home Servers ####
Mon Aug 26 15:01:09 2013 : Debug:  proxy server {
Mon Aug 26 15:01:09 2013 : Debug:     retry_delay = 5
Mon Aug 26 15:01:09 2013 : Debug:     retry_count = 3
Mon Aug 26 15:01:09 2013 : Debug:     default_fallback = no
Mon Aug 26 15:01:09 2013 : Debug:     dead_time = 120
Mon Aug 26 15:01:09 2013 : Debug:     wake_all_if_all_dead = no
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug:  home_server localhost {
Mon Aug 26 15:01:09 2013 : Debug:     ipaddr = 127.0.0.1
Mon Aug 26 15:01:09 2013 : Debug:     port = 1812
Mon Aug 26 15:01:09 2013 : Debug:     type = "auth"
Mon Aug 26 15:01:09 2013 : Debug:     secret = "testing123"
Mon Aug 26 15:01:09 2013 : Debug:     response_window = 20
Mon Aug 26 15:01:09 2013 : Debug:     max_outstanding = 65536
Mon Aug 26 15:01:09 2013 : Debug:     require_message_authenticator = yes
Mon Aug 26 15:01:09 2013 : Debug:     zombie_period = 40
Mon Aug 26 15:01:09 2013 : Debug:     status_check = "status-server"
Mon Aug 26 15:01:09 2013 : Debug:     ping_interval = 30
Mon Aug 26 15:01:09 2013 : Debug:     check_interval = 30
Mon Aug 26 15:01:09 2013 : Debug:     num_answers_to_alive = 3
Mon Aug 26 15:01:09 2013 : Debug:     num_pings_to_alive = 3
Mon Aug 26 15:01:09 2013 : Debug:     revive_interval = 120
Mon Aug 26 15:01:09 2013 : Debug:     status_check_timeout = 4
Mon Aug 26 15:01:09 2013 : Debug:     irt = 2
Mon Aug 26 15:01:09 2013 : Debug:     mrt = 16
Mon Aug 26 15:01:09 2013 : Debug:     mrc = 5
Mon Aug 26 15:01:09 2013 : Debug:     mrd = 30
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug:  home_server_pool my_auth_failover {
Mon Aug 26 15:01:09 2013 : Debug:     type = fail-over
Mon Aug 26 15:01:09 2013 : Debug:     home_server = localhost
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug:  realm example.com {
Mon Aug 26 15:01:09 2013 : Debug:     auth_pool = my_auth_failover
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug:  realm LOCAL {
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug: radiusd: #### Loading Clients ####
Mon Aug 26 15:01:09 2013 : Debug:  client localhost {
Mon Aug 26 15:01:09 2013 : Debug:     ipaddr = 127.0.0.1
Mon Aug 26 15:01:09 2013 : Debug:     require_message_authenticator = no
Mon Aug 26 15:01:09 2013 : Debug:     secret = "testing123"
Mon Aug 26 15:01:09 2013 : Debug:     nastype = "other"
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug: radiusd: #### Instantiating modules ####
Mon Aug 26 15:01:09 2013 : Debug:  instantiate {
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_exec, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_exec
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Mon Aug 26 15:01:09 2013 : Debug:   exec {
Mon Aug 26 15:01:09 2013 : Debug:     wait = no
Mon Aug 26 15:01:09 2013 : Debug:     input_pairs = "request"
Mon Aug 26 15:01:09 2013 : Debug:     shell_escape = yes
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_expr, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_expr
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_expiration
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Mon Aug 26 15:01:09 2013 : Debug:   expiration {
Mon Aug 26 15:01:09 2013 : Debug:     reply-message = "Password Has Expired  "
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_logintime
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Mon Aug 26 15:01:09 2013 : Debug:   logintime {
Mon Aug 26 15:01:09 2013 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Mon Aug 26 15:01:09 2013 : Debug:     minimum-timeout = 60
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  }
Mon Aug 26 15:01:09 2013 : Debug: radiusd: #### Loading Virtual Servers ####
Mon Aug 26 15:01:09 2013 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Mon Aug 26 15:01:09 2013 : Debug:  modules {
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_pap, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_pap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Mon Aug 26 15:01:09 2013 : Debug:   pap {
Mon Aug 26 15:01:09 2013 : Debug:     encryption_scheme = "auto"
Mon Aug 26 15:01:09 2013 : Debug:     auto_header = no
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_chap, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_chap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_mschap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Mon Aug 26 15:01:09 2013 : Debug:   mschap {
Mon Aug 26 15:01:09 2013 : Debug:     use_mppe = yes
Mon Aug 26 15:01:09 2013 : Debug:     require_encryption = no
Mon Aug 26 15:01:09 2013 : Debug:     require_strong = no
Mon Aug 26 15:01:09 2013 : Debug:     with_ntdomain_hack = no
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_unix, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_unix
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Mon Aug 26 15:01:09 2013 : Debug:   unix {
Mon Aug 26 15:01:09 2013 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_eap, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_eap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Mon Aug 26 15:01:09 2013 : Debug:   eap {
Mon Aug 26 15:01:09 2013 : Debug:     default_eap_type = "md5"
Mon Aug 26 15:01:09 2013 : Debug:     timer_expire = 60
Mon Aug 26 15:01:09 2013 : Debug:     ignore_unknown_eap_types = no
Mon Aug 26 15:01:09 2013 : Debug:     cisco_accounting_username_bug = no
Mon Aug 26 15:01:09 2013 : Debug:     max_sessions = 4096
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_md5
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-md5
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_leap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-leap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-gtc
Mon Aug 26 15:01:09 2013 : Debug:    gtc {
Mon Aug 26 15:01:09 2013 : Debug:     challenge = "Password: "
Mon Aug 26 15:01:09 2013 : Debug:     auth_type = "PAP"
Mon Aug 26 15:01:09 2013 : Debug:    }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_tls
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-tls
Mon Aug 26 15:01:09 2013 : Debug:    tls {
Mon Aug 26 15:01:09 2013 : Debug:     rsa_key_exchange = no
Mon Aug 26 15:01:09 2013 : Debug:     dh_key_exchange = yes
Mon Aug 26 15:01:09 2013 : Debug:     rsa_key_length = 512
Mon Aug 26 15:01:09 2013 : Debug:     dh_key_length = 512
Mon Aug 26 15:01:09 2013 : Debug:     verify_depth = 0
Mon Aug 26 15:01:09 2013 : Debug:     CA_path = "/etc/freeradius/certs"
Mon Aug 26 15:01:09 2013 : Debug:     pem_file_type = yes
Mon Aug 26 15:01:09 2013 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Mon Aug 26 15:01:09 2013 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Mon Aug 26 15:01:09 2013 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Mon Aug 26 15:01:09 2013 : Debug:     private_key_password = "whatever"
Mon Aug 26 15:01:09 2013 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Mon Aug 26 15:01:09 2013 : Debug:     random_file = "/dev/urandom"
Mon Aug 26 15:01:09 2013 : Debug:     fragment_size = 1024
Mon Aug 26 15:01:09 2013 : Debug:     include_length = yes
Mon Aug 26 15:01:09 2013 : Debug:     check_crl = no
Mon Aug 26 15:01:09 2013 : Debug:     cipher_list = "DEFAULT"
Mon Aug 26 15:01:09 2013 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Mon Aug 26 15:01:09 2013 : Debug:     cache {
Mon Aug 26 15:01:09 2013 : Debug:     enable = no
Mon Aug 26 15:01:09 2013 : Debug:     lifetime = 24
Mon Aug 26 15:01:09 2013 : Debug:     max_entries = 255
Mon Aug 26 15:01:09 2013 : Debug:     }
Mon Aug 26 15:01:09 2013 : Debug:     verify {
Mon Aug 26 15:01:09 2013 : Debug:     }
Mon Aug 26 15:01:09 2013 : Debug:    }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-ttls
Mon Aug 26 15:01:09 2013 : Debug:    ttls {
Mon Aug 26 15:01:09 2013 : Debug:     default_eap_type = "md5"
Mon Aug 26 15:01:09 2013 : Debug:     copy_request_to_tunnel = no
Mon Aug 26 15:01:09 2013 : Debug:     use_tunneled_reply = no
Mon Aug 26 15:01:09 2013 : Debug:     virtual_server = "inner-tunnel"
Mon Aug 26 15:01:09 2013 : Debug:     include_length = yes
Mon Aug 26 15:01:09 2013 : Debug:    }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_peap
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-peap
Mon Aug 26 15:01:09 2013 : Debug:    peap {
Mon Aug 26 15:01:09 2013 : Debug:     default_eap_type = "mschapv2"
Mon Aug 26 15:01:09 2013 : Debug:     copy_request_to_tunnel = no
Mon Aug 26 15:01:09 2013 : Debug:     use_tunneled_reply = no
Mon Aug 26 15:01:09 2013 : Debug:     proxy_tunneled_request_as_eap = yes
Mon Aug 26 15:01:09 2013 : Debug:     virtual_server = "inner-tunnel"
Mon Aug 26 15:01:09 2013 : Debug:    }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating eap-mschapv2
Mon Aug 26 15:01:09 2013 : Debug:    mschapv2 {
Mon Aug 26 15:01:09 2013 : Debug:     with_ntdomain_hack = no
Mon Aug 26 15:01:09 2013 : Debug:    }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_realm, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_realm
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Mon Aug 26 15:01:09 2013 : Debug:   realm suffix {
Mon Aug 26 15:01:09 2013 : Debug:     format = "suffix"
Mon Aug 26 15:01:09 2013 : Debug:     delimiter = "@"
Mon Aug 26 15:01:09 2013 : Debug:     ignore_default = no
Mon Aug 26 15:01:09 2013 : Debug:     ignore_null = no
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_files, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_files
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Mon Aug 26 15:01:09 2013 : Debug:   files {
Mon Aug 26 15:01:09 2013 : Debug:     usersfile = "/etc/freeradius/users"
Mon Aug 26 15:01:09 2013 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Mon Aug 26 15:01:09 2013 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Mon Aug 26 15:01:09 2013 : Debug:     compat = "no"
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking session {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_radutmp
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Mon Aug 26 15:01:09 2013 : Debug:   radutmp {
Mon Aug 26 15:01:09 2013 : Debug:     filename = "/var/log/freeradius/radutmp"
Mon Aug 26 15:01:09 2013 : Debug:     username = "%{User-Name}"
Mon Aug 26 15:01:09 2013 : Debug:     case_sensitive = yes
Mon Aug 26 15:01:09 2013 : Debug:     check_with_nas = yes
Mon Aug 26 15:01:09 2013 : Debug:     perm = 384
Mon Aug 26 15:01:09 2013 : Debug:     callerid = yes
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking post-proxy {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking post-auth {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_attr_filter
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Mon Aug 26 15:01:09 2013 : Debug:   attr_filter attr_filter.access_reject {
Mon Aug 26 15:01:09 2013 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Mon Aug 26 15:01:09 2013 : Debug:     key = "%{User-Name}"
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  } # modules
Mon Aug 26 15:01:09 2013 : Debug: } # server
Mon Aug 26 15:01:09 2013 : Debug: server { # from file /etc/freeradius/radiusd.conf
Mon Aug 26 15:01:09 2013 : Debug:  modules {
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_digest, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_digest
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_preprocess
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Mon Aug 26 15:01:09 2013 : Debug:   preprocess {
Mon Aug 26 15:01:09 2013 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Mon Aug 26 15:01:09 2013 : Debug:     hints = "/etc/freeradius/hints"
Mon Aug 26 15:01:09 2013 : Debug:     with_ascend_hack = no
Mon Aug 26 15:01:09 2013 : Debug:     ascend_channels_per_line = 23
Mon Aug 26 15:01:09 2013 : Debug:     with_ntdomain_hack = no
Mon Aug 26 15:01:09 2013 : Debug:     with_specialix_jetstream_hack = no
Mon Aug 26 15:01:09 2013 : Debug:     with_cisco_vsa_hack = no
Mon Aug 26 15:01:09 2013 : Debug:     with_alvarion_vsa_hack = no
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking preacct {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_acct_unique
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Mon Aug 26 15:01:09 2013 : Debug:   acct_unique {
Mon Aug 26 15:01:09 2013 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking accounting {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:     (Loaded rlm_detail, checking if it's valid)
Mon Aug 26 15:01:09 2013 : Debug:  Module: Linked to module rlm_detail
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Mon Aug 26 15:01:09 2013 : Debug:   detail {
Mon Aug 26 15:01:09 2013 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Mon Aug 26 15:01:09 2013 : Debug:     header = "%t"
Mon Aug 26 15:01:09 2013 : Debug:     detailperm = 384
Mon Aug 26 15:01:09 2013 : Debug:     dirperm = 493
Mon Aug 26 15:01:09 2013 : Debug:     locking = no
Mon Aug 26 15:01:09 2013 : Debug:     log_packet_header = no
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
Mon Aug 26 15:01:09 2013 : Debug:   attr_filter attr_filter.accounting_response {
Mon Aug 26 15:01:09 2013 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Mon Aug 26 15:01:09 2013 : Debug:     key = "%{User-Name}"
Mon Aug 26 15:01:09 2013 : Debug:   }
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking session {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking post-proxy {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:  Module: Checking post-auth {...} for more modules to load
Mon Aug 26 15:01:09 2013 : Debug:  } # modules
Mon Aug 26 15:01:09 2013 : Debug: } # server
Mon Aug 26 15:01:09 2013 : Debug: radiusd: #### Opening IP addresses and Ports ####
Mon Aug 26 15:01:09 2013 : Debug: listen {
Mon Aug 26 15:01:09 2013 : Debug:     type = "auth"
Mon Aug 26 15:01:09 2013 : Debug:     ipaddr = *
Mon Aug 26 15:01:09 2013 : Debug:     port = 0
Mon Aug 26 15:01:09 2013 : Debug: }
Mon Aug 26 15:01:09 2013 : Debug: listen {
Mon Aug 26 15:01:09 2013 : Debug:     type = "acct"
Mon Aug 26 15:01:09 2013 : Debug:     ipaddr = *
Mon Aug 26 15:01:09 2013 : Debug:     port = 0
Mon Aug 26 15:01:09 2013 : Debug: }
Mon Aug 26 15:01:09 2013 : Debug: listen {
Mon Aug 26 15:01:09 2013 : Debug:     type = "auth"
Mon Aug 26 15:01:09 2013 : Debug:     ipaddr = 127.0.0.1
Mon Aug 26 15:01:09 2013 : Debug:     port = 18120
Mon Aug 26 15:01:09 2013 : Debug: }
Mon Aug 26 15:01:09 2013 : Debug: Listening on authentication address * port 1812
Mon Aug 26 15:01:09 2013 : Debug: Listening on accounting address * port 1813
Mon Aug 26 15:01:09 2013 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Mon Aug 26 15:01:09 2013 : Debug: Listening on proxy address * port 1814
Mon Aug 26 15:01:09 2013 : Info: Ready to process requests.



---

### Post by laughmo on 2013-08-26
please check line 152 in file 

/etc/freeradius/sites-enabled/default

it should be like this, with file line uncommented:

#  Read the 'users' file
    files

i need to the debug results after you run the raddtest command

---

### Post by ahmy2 on 2013-09-02
> **laughmo said:**
> please check line 152 in file 

/etc/freeradius/sites-enabled/default

it should be like this, with file line uncommented:

#  Read the 'users' file
    files

i need to the debug results after you run the raddtest command



Hello Laughmo,

Sorry it took me 2 long to post back the results, i was away from my test enviroment i`ve checed the ""default"" file i didn`t chnage nothing in there cuz it was already as u instructed 

> #
    #  Pull crypt'd passwords from /etc/passwd or /etc/shadow,
    #  using the system API's to get the password.  If you want
    #  to read /etc/passwd or /etc/shadow directly, see the
    #  passwd module in radiusd.conf.
    #
#    unix

    [COLOR=#ff0000]#
    #  Read the 'users' file
    files
[/COLOR]
    #
    #  Look in an SQL database.  The schema of the database
    #  is meant to mirror the "users" file.
    #
    #  See "Authorization Queries" in sql.conf
#    sql

I`m still getting the same error below : 

> sudo radtest "John Doe" hello 127.0.0.1 0 testing123
Sending Access-Request of id 249 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
rad_recv: Access-Reject packet from host 127.0.0.1 port 1812, id=249, length=20






Cheers

---

### Post by laughmo on 2013-09-02
please post the output of the debug freeradius -XXX

---

### Post by ahmy2 on 2013-09-03
> **laughmo said:**
> please post the output of the debug freeradius -XXX


Here`s the log : 

```
root@test:~# freeradius -XXX |tee testlog.log
Tue Sep  3 11:25:13 2013 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Tue Sep  3 11:25:13 2013 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Tue Sep  3 11:25:13 2013 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Tue Sep  3 11:25:13 2013 : Info: PARTICULAR PURPOSE. 
Tue Sep  3 11:25:13 2013 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Tue Sep  3 11:25:13 2013 : Info: GNU General Public License v2. 
Tue Sep  3 11:25:13 2013 : Info: Starting - reading configuration files ...
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/radiusd.conf
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/proxy.conf
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/clients.conf
Tue Sep  3 11:25:13 2013 : Debug: including files in directory /etc/freeradius/modules/
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/expiration
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/detail
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/always
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/echo
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/unix
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/mschap
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/smsotp
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/sql_log
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/wimax
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/logintime
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/ippool
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/checkval
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/expr
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/perl
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/radutmp
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/krb5
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/files
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/cui
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/ldap
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/preprocess
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/pap
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/linelog
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/detail.log
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/pam
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/digest
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/exec
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/passwd
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/chap
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/policy
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/counter
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/etc_group
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/realm
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/modules/otp
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/eap.conf
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/policy.conf
Tue Sep  3 11:25:13 2013 : Debug: including files in directory /etc/freeradius/sites-enabled/
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Tue Sep  3 11:25:13 2013 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Tue Sep  3 11:25:13 2013 : Debug: main {
Tue Sep  3 11:25:13 2013 : Debug:     user = "freerad"
Tue Sep  3 11:25:13 2013 : Debug:     group = "freerad"
Tue Sep  3 11:25:13 2013 : Debug:     allow_core_dumps = no
Tue Sep  3 11:25:13 2013 : Debug: }
Tue Sep  3 11:25:13 2013 : Debug: including dictionary file /etc/freeradius/dictionary
Tue Sep  3 11:25:13 2013 : Debug: main {
Tue Sep  3 11:25:13 2013 : Debug:     prefix = "/usr"
Tue Sep  3 11:25:13 2013 : Debug:     localstatedir = "/var"
Tue Sep  3 11:25:13 2013 : Debug:     logdir = "/var/log/freeradius"
Tue Sep  3 11:25:13 2013 : Debug:     libdir = "/usr/lib/freeradius"
Tue Sep  3 11:25:13 2013 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Tue Sep  3 11:25:13 2013 : Debug:     hostname_lookups = no
Tue Sep  3 11:25:13 2013 : Debug:     max_request_time = 30
Tue Sep  3 11:25:13 2013 : Debug:     cleanup_delay = 5
Tue Sep  3 11:25:13 2013 : Debug:     max_requests = 1024
Tue Sep  3 11:25:13 2013 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Tue Sep  3 11:25:13 2013 : Debug:     checkrad = "/usr/sbin/checkrad"
Tue Sep  3 11:25:13 2013 : Debug:     debug_level = 0
Tue Sep  3 11:25:13 2013 : Debug:     proxy_requests = yes
Tue Sep  3 11:25:13 2013 : Debug:  log {
Tue Sep  3 11:25:13 2013 : Debug:     stripped_names = no
Tue Sep  3 11:25:13 2013 : Debug:     auth = no
Tue Sep  3 11:25:13 2013 : Debug:     auth_badpass = no
Tue Sep  3 11:25:13 2013 : Debug:     auth_goodpass = no
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug:  security {
Tue Sep  3 11:25:13 2013 : Debug:     max_attributes = 200
Tue Sep  3 11:25:13 2013 : Debug:     reject_delay = 1
Tue Sep  3 11:25:13 2013 : Debug:     status_server = yes
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug: }
Tue Sep  3 11:25:13 2013 : Debug: radiusd: #### Loading Realms and Home Servers ####
Tue Sep  3 11:25:13 2013 : Debug:  proxy server {
Tue Sep  3 11:25:13 2013 : Debug:     retry_delay = 5
Tue Sep  3 11:25:13 2013 : Debug:     retry_count = 3
Tue Sep  3 11:25:13 2013 : Debug:     default_fallback = no
Tue Sep  3 11:25:13 2013 : Debug:     dead_time = 120
Tue Sep  3 11:25:13 2013 : Debug:     wake_all_if_all_dead = no
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug:  home_server localhost {
Tue Sep  3 11:25:13 2013 : Debug:     ipaddr = 127.0.0.1
Tue Sep  3 11:25:13 2013 : Debug:     port = 1812
Tue Sep  3 11:25:13 2013 : Debug:     type = "auth"
Tue Sep  3 11:25:13 2013 : Debug:     secret = "testing123"
Tue Sep  3 11:25:13 2013 : Debug:     response_window = 20
Tue Sep  3 11:25:13 2013 : Debug:     max_outstanding = 65536
Tue Sep  3 11:25:13 2013 : Debug:     require_message_authenticator = yes
Tue Sep  3 11:25:13 2013 : Debug:     zombie_period = 40
Tue Sep  3 11:25:13 2013 : Debug:     status_check = "status-server"
Tue Sep  3 11:25:13 2013 : Debug:     ping_interval = 30
Tue Sep  3 11:25:13 2013 : Debug:     check_interval = 30
Tue Sep  3 11:25:13 2013 : Debug:     num_answers_to_alive = 3
Tue Sep  3 11:25:13 2013 : Debug:     num_pings_to_alive = 3
Tue Sep  3 11:25:13 2013 : Debug:     revive_interval = 120
Tue Sep  3 11:25:13 2013 : Debug:     status_check_timeout = 4
Tue Sep  3 11:25:13 2013 : Debug:     irt = 2
Tue Sep  3 11:25:13 2013 : Debug:     mrt = 16
Tue Sep  3 11:25:13 2013 : Debug:     mrc = 5
Tue Sep  3 11:25:13 2013 : Debug:     mrd = 30
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug:  home_server_pool my_auth_failover {
Tue Sep  3 11:25:13 2013 : Debug:     type = fail-over
Tue Sep  3 11:25:13 2013 : Debug:     home_server = localhost
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug:  realm example.com {
Tue Sep  3 11:25:13 2013 : Debug:     auth_pool = my_auth_failover
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug:  realm LOCAL {
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug: radiusd: #### Loading Clients ####
Tue Sep  3 11:25:13 2013 : Debug:  client localhost {
Tue Sep  3 11:25:13 2013 : Debug:     ipaddr = 127.0.0.1
Tue Sep  3 11:25:13 2013 : Debug:     require_message_authenticator = no
Tue Sep  3 11:25:13 2013 : Debug:     secret = "testing123"
Tue Sep  3 11:25:13 2013 : Debug:     nastype = "other"
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug: radiusd: #### Instantiating modules ####
Tue Sep  3 11:25:13 2013 : Debug:  instantiate {
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_exec, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_exec
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Tue Sep  3 11:25:13 2013 : Debug:   exec {
Tue Sep  3 11:25:13 2013 : Debug:     wait = no
Tue Sep  3 11:25:13 2013 : Debug:     input_pairs = "request"
Tue Sep  3 11:25:13 2013 : Debug:     shell_escape = yes
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_expr, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_expr
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_expiration
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Tue Sep  3 11:25:13 2013 : Debug:   expiration {
Tue Sep  3 11:25:13 2013 : Debug:     reply-message = "Password Has Expired  "
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_logintime
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Tue Sep  3 11:25:13 2013 : Debug:   logintime {
Tue Sep  3 11:25:13 2013 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Tue Sep  3 11:25:13 2013 : Debug:     minimum-timeout = 60
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  }
Tue Sep  3 11:25:13 2013 : Debug: radiusd: #### Loading Virtual Servers ####
Tue Sep  3 11:25:13 2013 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Tue Sep  3 11:25:13 2013 : Debug:  modules {
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_pap, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_pap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Tue Sep  3 11:25:13 2013 : Debug:   pap {
Tue Sep  3 11:25:13 2013 : Debug:     encryption_scheme = "auto"
Tue Sep  3 11:25:13 2013 : Debug:     auto_header = no
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_chap, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_chap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_mschap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Tue Sep  3 11:25:13 2013 : Debug:   mschap {
Tue Sep  3 11:25:13 2013 : Debug:     use_mppe = yes
Tue Sep  3 11:25:13 2013 : Debug:     require_encryption = no
Tue Sep  3 11:25:13 2013 : Debug:     require_strong = no
Tue Sep  3 11:25:13 2013 : Debug:     with_ntdomain_hack = no
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_unix, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_unix
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Tue Sep  3 11:25:13 2013 : Debug:   unix {
Tue Sep  3 11:25:13 2013 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_eap, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_eap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Tue Sep  3 11:25:13 2013 : Debug:   eap {
Tue Sep  3 11:25:13 2013 : Debug:     default_eap_type = "md5"
Tue Sep  3 11:25:13 2013 : Debug:     timer_expire = 60
Tue Sep  3 11:25:13 2013 : Debug:     ignore_unknown_eap_types = no
Tue Sep  3 11:25:13 2013 : Debug:     cisco_accounting_username_bug = no
Tue Sep  3 11:25:13 2013 : Debug:     max_sessions = 4096
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_md5
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-md5
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_leap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-leap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-gtc
Tue Sep  3 11:25:13 2013 : Debug:    gtc {
Tue Sep  3 11:25:13 2013 : Debug:     challenge = "Password: "
Tue Sep  3 11:25:13 2013 : Debug:     auth_type = "PAP"
Tue Sep  3 11:25:13 2013 : Debug:    }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_tls
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-tls
Tue Sep  3 11:25:13 2013 : Debug:    tls {
Tue Sep  3 11:25:13 2013 : Debug:     rsa_key_exchange = no
Tue Sep  3 11:25:13 2013 : Debug:     dh_key_exchange = yes
Tue Sep  3 11:25:13 2013 : Debug:     rsa_key_length = 512
Tue Sep  3 11:25:13 2013 : Debug:     dh_key_length = 512
Tue Sep  3 11:25:13 2013 : Debug:     verify_depth = 0
Tue Sep  3 11:25:13 2013 : Debug:     CA_path = "/etc/freeradius/certs"
Tue Sep  3 11:25:13 2013 : Debug:     pem_file_type = yes
Tue Sep  3 11:25:13 2013 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Tue Sep  3 11:25:13 2013 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Tue Sep  3 11:25:13 2013 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Tue Sep  3 11:25:13 2013 : Debug:     private_key_password = "whatever"
Tue Sep  3 11:25:13 2013 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Tue Sep  3 11:25:13 2013 : Debug:     random_file = "/dev/urandom"
Tue Sep  3 11:25:13 2013 : Debug:     fragment_size = 1024
Tue Sep  3 11:25:13 2013 : Debug:     include_length = yes
Tue Sep  3 11:25:13 2013 : Debug:     check_crl = no
Tue Sep  3 11:25:13 2013 : Debug:     cipher_list = "DEFAULT"
Tue Sep  3 11:25:13 2013 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Tue Sep  3 11:25:13 2013 : Debug:     cache {
Tue Sep  3 11:25:13 2013 : Debug:     enable = no
Tue Sep  3 11:25:13 2013 : Debug:     lifetime = 24
Tue Sep  3 11:25:13 2013 : Debug:     max_entries = 255
Tue Sep  3 11:25:13 2013 : Debug:     }
Tue Sep  3 11:25:13 2013 : Debug:     verify {
Tue Sep  3 11:25:13 2013 : Debug:     }
Tue Sep  3 11:25:13 2013 : Debug:    }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-ttls
Tue Sep  3 11:25:13 2013 : Debug:    ttls {
Tue Sep  3 11:25:13 2013 : Debug:     default_eap_type = "md5"
Tue Sep  3 11:25:13 2013 : Debug:     copy_request_to_tunnel = no
Tue Sep  3 11:25:13 2013 : Debug:     use_tunneled_reply = no
Tue Sep  3 11:25:13 2013 : Debug:     virtual_server = "inner-tunnel"
Tue Sep  3 11:25:13 2013 : Debug:     include_length = yes
Tue Sep  3 11:25:13 2013 : Debug:    }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_peap
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-peap
Tue Sep  3 11:25:13 2013 : Debug:    peap {
Tue Sep  3 11:25:13 2013 : Debug:     default_eap_type = "mschapv2"
Tue Sep  3 11:25:13 2013 : Debug:     copy_request_to_tunnel = no
Tue Sep  3 11:25:13 2013 : Debug:     use_tunneled_reply = no
Tue Sep  3 11:25:13 2013 : Debug:     proxy_tunneled_request_as_eap = yes
Tue Sep  3 11:25:13 2013 : Debug:     virtual_server = "inner-tunnel"
Tue Sep  3 11:25:13 2013 : Debug:    }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating eap-mschapv2
Tue Sep  3 11:25:13 2013 : Debug:    mschapv2 {
Tue Sep  3 11:25:13 2013 : Debug:     with_ntdomain_hack = no
Tue Sep  3 11:25:13 2013 : Debug:    }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_realm, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_realm
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Tue Sep  3 11:25:13 2013 : Debug:   realm suffix {
Tue Sep  3 11:25:13 2013 : Debug:     format = "suffix"
Tue Sep  3 11:25:13 2013 : Debug:     delimiter = "@"
Tue Sep  3 11:25:13 2013 : Debug:     ignore_default = no
Tue Sep  3 11:25:13 2013 : Debug:     ignore_null = no
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_files, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_files
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Tue Sep  3 11:25:13 2013 : Debug:   files {
Tue Sep  3 11:25:13 2013 : Debug:     usersfile = "/etc/freeradius/users"
Tue Sep  3 11:25:13 2013 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Tue Sep  3 11:25:13 2013 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Tue Sep  3 11:25:13 2013 : Debug:     compat = "no"
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking session {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_radutmp
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Tue Sep  3 11:25:13 2013 : Debug:   radutmp {
Tue Sep  3 11:25:13 2013 : Debug:     filename = "/var/log/freeradius/radutmp"
Tue Sep  3 11:25:13 2013 : Debug:     username = "%{User-Name}"
Tue Sep  3 11:25:13 2013 : Debug:     case_sensitive = yes
Tue Sep  3 11:25:13 2013 : Debug:     check_with_nas = yes
Tue Sep  3 11:25:13 2013 : Debug:     perm = 384
Tue Sep  3 11:25:13 2013 : Debug:     callerid = yes
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking post-proxy {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking post-auth {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_attr_filter
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Tue Sep  3 11:25:13 2013 : Debug:   attr_filter attr_filter.access_reject {
Tue Sep  3 11:25:13 2013 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Tue Sep  3 11:25:13 2013 : Debug:     key = "%{User-Name}"
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  } # modules
Tue Sep  3 11:25:13 2013 : Debug: } # server
Tue Sep  3 11:25:13 2013 : Debug: server { # from file /etc/freeradius/radiusd.conf
Tue Sep  3 11:25:13 2013 : Debug:  modules {
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_digest, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_digest
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_preprocess
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Tue Sep  3 11:25:13 2013 : Debug:   preprocess {
Tue Sep  3 11:25:13 2013 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Tue Sep  3 11:25:13 2013 : Debug:     hints = "/etc/freeradius/hints"
Tue Sep  3 11:25:13 2013 : Debug:     with_ascend_hack = no
Tue Sep  3 11:25:13 2013 : Debug:     ascend_channels_per_line = 23
Tue Sep  3 11:25:13 2013 : Debug:     with_ntdomain_hack = no
Tue Sep  3 11:25:13 2013 : Debug:     with_specialix_jetstream_hack = no
Tue Sep  3 11:25:13 2013 : Debug:     with_cisco_vsa_hack = no
Tue Sep  3 11:25:13 2013 : Debug:     with_alvarion_vsa_hack = no
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking preacct {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_acct_unique
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Tue Sep  3 11:25:13 2013 : Debug:   acct_unique {
Tue Sep  3 11:25:13 2013 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking accounting {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:     (Loaded rlm_detail, checking if it's valid)
Tue Sep  3 11:25:13 2013 : Debug:  Module: Linked to module rlm_detail
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Tue Sep  3 11:25:13 2013 : Debug:   detail {
Tue Sep  3 11:25:13 2013 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Tue Sep  3 11:25:13 2013 : Debug:     header = "%t"
Tue Sep  3 11:25:13 2013 : Debug:     detailperm = 384
Tue Sep  3 11:25:13 2013 : Debug:     dirperm = 493
Tue Sep  3 11:25:13 2013 : Debug:     locking = no
Tue Sep  3 11:25:13 2013 : Debug:     log_packet_header = no
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
Tue Sep  3 11:25:13 2013 : Debug:   attr_filter attr_filter.accounting_response {
Tue Sep  3 11:25:13 2013 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Tue Sep  3 11:25:13 2013 : Debug:     key = "%{User-Name}"
Tue Sep  3 11:25:13 2013 : Debug:   }
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking session {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking post-proxy {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:  Module: Checking post-auth {...} for more modules to load
Tue Sep  3 11:25:13 2013 : Debug:  } # modules
Tue Sep  3 11:25:13 2013 : Debug: } # server
Tue Sep  3 11:25:13 2013 : Debug: radiusd: #### Opening IP addresses and Ports ####
Tue Sep  3 11:25:13 2013 : Debug: listen {
Tue Sep  3 11:25:13 2013 : Debug:     type = "auth"
Tue Sep  3 11:25:13 2013 : Debug:     ipaddr = *
Tue Sep  3 11:25:13 2013 : Debug:     port = 0
Tue Sep  3 11:25:13 2013 : Error: Failed binding to authentication address * port 1812: Address already in use 
Tue Sep  3 11:25:13 2013 : Error: /etc/freeradius/radiusd.conf[240]: Error binding to port for 0.0.0.0 port 1812


```

---

### Post by laughmo on 2013-09-03
you have an error as seen here:
Tue Sep  3 11:25:13 2013 : Debug: radiusd: #### Opening IP addresses and Ports ####
Tue Sep  3 11:25:13 2013 : Debug: listen {
Tue Sep  3 11:25:13 2013 : Debug:     type = "auth"
Tue Sep  3 11:25:13 2013 : Debug:     ipaddr = *
Tue Sep  3 11:25:13 2013 : Debug:     port = 0
Tue Sep  3 11:25:13 2013 : Error: Failed binding to authentication address * port 1812: Address already in use 
Tue Sep  3 11:25:13 2013 : Error: /etc/freeradius/radiusd.conf[240]: Error binding to port for 0.0.0.0 port 1812

please stop freeradius

 sudo /etc/init.d/freeradius stop

then run the command
 sudo freeradius -XXX | tee radiuslog.txt

it should start successfully with last line showing "Ready to process requests"

then run the radtest command

then paste the contents of radiuslog.txt here

---

### Post by 0651 on 2013-09-05
In step Daloradius Quick Start, I did not find the columns for,


"Check Attributes
Simultaneous-Use = 1
Max-All-Session = 3600
[this is in seconds, for 60mins = 3600seconds]
Session-Timeout = 3600 "


and


"Reply Attributes
Session-Timeout = 3600
Idle-Timeout = 60
Acct-Interim-Interval = 120 "


Is it because I use daloradius-0.9-9.tar.gz, is not the same as you are using daloradius-0.9-9-rc1.tar.gz?


Please help, -


Thank you.

---

### Post by laughmo on 2013-09-05
your freeradius should first run without any error. are you able to get it to run?

---

### Post by 0651 on 2013-09-05
The error message when I do a debug

"Thu Sep  5 21:54:13 2013 : Debug:   }Thu Sep  5 21:54:13 2013 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Thu Sep  5 21:54:13 2013 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Thu Sep  5 21:54:13 2013 : Debug: rlm_sql (sql): starting 0
Thu Sep  5 21:54:13 2013 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Thu Sep  5 21:54:13 2013 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Thu Sep  5 21:54:13 2013 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Thu Sep  5 21:54:13 2013 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Thu Sep  5 21:54:13 2013 : Error: rlm_sql (sql): Failed to connect DB handle #0
Thu Sep  5 21:54:13 2013 : Debug: rlm_sql (sql): starting 1
Thu Sep  5 21:54:13 2013 : Debug: rlm_sql (sql): starting 2
Thu Sep  5 21:54:13 2013 : Debug: rlm_sql (sql): starting 3
Thu Sep  5 21:54:13 2013 : Debug: rlm_sql (sql): starting 4
Thu Sep  5 21:54:13 2013 : Debug: rlm_sql (sql): Failed to connect to any SQL server."

and this

"Thu Sep 5 21:54:13 2013: Debug: port = 0
Thu Sep 5 21:54:13 2013: Error: Failed binding to authentication address * port 1812: Address already in use
Thu Sep 5 21:54:13 2013: Error: / etc / freeradius / radiusd.conf [240]: Error binding to port for 0.0.0.0 port 1812 "


what should I do?

I am very thankful before, you have a lot of help ...

---

### Post by laughmo on 2013-09-06
send me a compressed file of the directory /etc/freeradius

# tar cfvz freeradius.tar.gz /etc/freeradius

---

### Post by 0651 on 2013-09-07
> **laughmo said:**
> send me a compressed file of the directory /etc/freeradius

# tar cfvz freeradius.tar.gz /etc/freeradius

I've managed to attach the file, -: D

---

### Post by ahmy2 on 2013-09-08
Hello everyone....

I can sucssefully stop and start freeradius with no errors 


```
Sun Sep  8 12:27:06 2013 : Info: GNU General Public License v2. 
Sun Sep  8 12:27:06 2013 : Info: Starting - reading configuration files ...
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/proxy.conf
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/clients.conf
Sun Sep  8 12:27:06 2013 : Debug: including files in directory /etc/freeradius/modules/
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/expiration
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/detail
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/always
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/echo
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/unix
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/mschap
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/wimax
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/logintime
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/ippool
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/checkval
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/expr
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/perl
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/krb5
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/files
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/cui
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/ldap
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/pap
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/linelog
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/pam
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/digest
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/exec
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/passwd
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/chap
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/policy
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/counter
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/realm
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/modules/otp
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/eap.conf
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/policy.conf
Sun Sep  8 12:27:06 2013 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sun Sep  8 12:27:06 2013 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sun Sep  8 12:27:06 2013 : Debug: main {
Sun Sep  8 12:27:06 2013 : Debug:     user = "freerad"
Sun Sep  8 12:27:06 2013 : Debug:     group = "freerad"
Sun Sep  8 12:27:06 2013 : Debug:     allow_core_dumps = no
Sun Sep  8 12:27:06 2013 : Debug: }
Sun Sep  8 12:27:06 2013 : Debug: including dictionary file /etc/freeradius/dictionary
Sun Sep  8 12:27:06 2013 : Debug: main {
Sun Sep  8 12:27:06 2013 : Debug:     prefix = "/usr"
Sun Sep  8 12:27:06 2013 : Debug:     localstatedir = "/var"
Sun Sep  8 12:27:06 2013 : Debug:     logdir = "/var/log/freeradius"
Sun Sep  8 12:27:06 2013 : Debug:     libdir = "/usr/lib/freeradius"
Sun Sep  8 12:27:06 2013 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sun Sep  8 12:27:06 2013 : Debug:     hostname_lookups = no
Sun Sep  8 12:27:06 2013 : Debug:     max_request_time = 30
Sun Sep  8 12:27:06 2013 : Debug:     cleanup_delay = 5
Sun Sep  8 12:27:06 2013 : Debug:     max_requests = 1024
Sun Sep  8 12:27:06 2013 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sun Sep  8 12:27:06 2013 : Debug:     checkrad = "/usr/sbin/checkrad"
Sun Sep  8 12:27:06 2013 : Debug:     debug_level = 0
Sun Sep  8 12:27:06 2013 : Debug:     proxy_requests = yes
Sun Sep  8 12:27:06 2013 : Debug:  log {
Sun Sep  8 12:27:06 2013 : Debug:     stripped_names = no
Sun Sep  8 12:27:06 2013 : Debug:     auth = no
Sun Sep  8 12:27:06 2013 : Debug:     auth_badpass = no
Sun Sep  8 12:27:06 2013 : Debug:     auth_goodpass = no
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug:  security {
Sun Sep  8 12:27:06 2013 : Debug:     max_attributes = 200
Sun Sep  8 12:27:06 2013 : Debug:     reject_delay = 1
Sun Sep  8 12:27:06 2013 : Debug:     status_server = yes
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug: }
Sun Sep  8 12:27:06 2013 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sun Sep  8 12:27:06 2013 : Debug:  proxy server {
Sun Sep  8 12:27:06 2013 : Debug:     retry_delay = 5
Sun Sep  8 12:27:06 2013 : Debug:     retry_count = 3
Sun Sep  8 12:27:06 2013 : Debug:     default_fallback = no
Sun Sep  8 12:27:06 2013 : Debug:     dead_time = 120
Sun Sep  8 12:27:06 2013 : Debug:     wake_all_if_all_dead = no
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug:  home_server localhost {
Sun Sep  8 12:27:06 2013 : Debug:     ipaddr = 127.0.0.1
Sun Sep  8 12:27:06 2013 : Debug:     port = 1812
Sun Sep  8 12:27:06 2013 : Debug:     type = "auth"
Sun Sep  8 12:27:06 2013 : Debug:     secret = "testing123"
Sun Sep  8 12:27:06 2013 : Debug:     response_window = 20
Sun Sep  8 12:27:06 2013 : Debug:     max_outstanding = 65536
Sun Sep  8 12:27:06 2013 : Debug:     require_message_authenticator = yes
Sun Sep  8 12:27:06 2013 : Debug:     zombie_period = 40
Sun Sep  8 12:27:06 2013 : Debug:     status_check = "status-server"
Sun Sep  8 12:27:06 2013 : Debug:     ping_interval = 30
Sun Sep  8 12:27:06 2013 : Debug:     check_interval = 30
Sun Sep  8 12:27:06 2013 : Debug:     num_answers_to_alive = 3
Sun Sep  8 12:27:06 2013 : Debug:     num_pings_to_alive = 3
Sun Sep  8 12:27:06 2013 : Debug:     revive_interval = 120
Sun Sep  8 12:27:06 2013 : Debug:     status_check_timeout = 4
Sun Sep  8 12:27:06 2013 : Debug:     irt = 2
Sun Sep  8 12:27:06 2013 : Debug:     mrt = 16
Sun Sep  8 12:27:06 2013 : Debug:     mrc = 5
Sun Sep  8 12:27:06 2013 : Debug:     mrd = 30
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug:  home_server_pool my_auth_failover {
Sun Sep  8 12:27:06 2013 : Debug:     type = fail-over
Sun Sep  8 12:27:06 2013 : Debug:     home_server = localhost
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug:  realm example.com {
Sun Sep  8 12:27:06 2013 : Debug:     auth_pool = my_auth_failover
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug:  realm LOCAL {
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug: radiusd: #### Loading Clients ####
Sun Sep  8 12:27:06 2013 : Debug:  client localhost {
Sun Sep  8 12:27:06 2013 : Debug:     ipaddr = 127.0.0.1
Sun Sep  8 12:27:06 2013 : Debug:     require_message_authenticator = no
Sun Sep  8 12:27:06 2013 : Debug:     secret = "testing123"
Sun Sep  8 12:27:06 2013 : Debug:     nastype = "other"
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug: radiusd: #### Instantiating modules ####
Sun Sep  8 12:27:06 2013 : Debug:  instantiate {
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_exec
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sun Sep  8 12:27:06 2013 : Debug:   exec {
Sun Sep  8 12:27:06 2013 : Debug:     wait = no
Sun Sep  8 12:27:06 2013 : Debug:     input_pairs = "request"
Sun Sep  8 12:27:06 2013 : Debug:     shell_escape = yes
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_expr
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_expiration
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sun Sep  8 12:27:06 2013 : Debug:   expiration {
Sun Sep  8 12:27:06 2013 : Debug:     reply-message = "Password Has Expired  "
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_logintime
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sun Sep  8 12:27:06 2013 : Debug:   logintime {
Sun Sep  8 12:27:06 2013 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sun Sep  8 12:27:06 2013 : Debug:     minimum-timeout = 60
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  }
Sun Sep  8 12:27:06 2013 : Debug: radiusd: #### Loading Virtual Servers ####
Sun Sep  8 12:27:06 2013 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sun Sep  8 12:27:06 2013 : Debug:  modules {
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_pap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sun Sep  8 12:27:06 2013 : Debug:   pap {
Sun Sep  8 12:27:06 2013 : Debug:     encryption_scheme = "auto"
Sun Sep  8 12:27:06 2013 : Debug:     auto_header = no
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_chap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_mschap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sun Sep  8 12:27:06 2013 : Debug:   mschap {
Sun Sep  8 12:27:06 2013 : Debug:     use_mppe = yes
Sun Sep  8 12:27:06 2013 : Debug:     require_encryption = no
Sun Sep  8 12:27:06 2013 : Debug:     require_strong = no
Sun Sep  8 12:27:06 2013 : Debug:     with_ntdomain_hack = no
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_unix
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sun Sep  8 12:27:06 2013 : Debug:   unix {
Sun Sep  8 12:27:06 2013 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_eap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sun Sep  8 12:27:06 2013 : Debug:   eap {
Sun Sep  8 12:27:06 2013 : Debug:     default_eap_type = "md5"
Sun Sep  8 12:27:06 2013 : Debug:     timer_expire = 60
Sun Sep  8 12:27:06 2013 : Debug:     ignore_unknown_eap_types = no
Sun Sep  8 12:27:06 2013 : Debug:     cisco_accounting_username_bug = no
Sun Sep  8 12:27:06 2013 : Debug:     max_sessions = 4096
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-md5
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-leap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-gtc
Sun Sep  8 12:27:06 2013 : Debug:    gtc {
Sun Sep  8 12:27:06 2013 : Debug:     challenge = "Password: "
Sun Sep  8 12:27:06 2013 : Debug:     auth_type = "PAP"
Sun Sep  8 12:27:06 2013 : Debug:    }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-tls
Sun Sep  8 12:27:06 2013 : Debug:    tls {
Sun Sep  8 12:27:06 2013 : Debug:     rsa_key_exchange = no
Sun Sep  8 12:27:06 2013 : Debug:     dh_key_exchange = yes
Sun Sep  8 12:27:06 2013 : Debug:     rsa_key_length = 512
Sun Sep  8 12:27:06 2013 : Debug:     dh_key_length = 512
Sun Sep  8 12:27:06 2013 : Debug:     verify_depth = 0
Sun Sep  8 12:27:06 2013 : Debug:     CA_path = "/etc/freeradius/certs"
Sun Sep  8 12:27:06 2013 : Debug:     pem_file_type = yes
Sun Sep  8 12:27:06 2013 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sun Sep  8 12:27:06 2013 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sun Sep  8 12:27:06 2013 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sun Sep  8 12:27:06 2013 : Debug:     private_key_password = "whatever"
Sun Sep  8 12:27:06 2013 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sun Sep  8 12:27:06 2013 : Debug:     random_file = "/dev/urandom"
Sun Sep  8 12:27:06 2013 : Debug:     fragment_size = 1024
Sun Sep  8 12:27:06 2013 : Debug:     include_length = yes
Sun Sep  8 12:27:06 2013 : Debug:     check_crl = no
Sun Sep  8 12:27:06 2013 : Debug:     cipher_list = "DEFAULT"
Sun Sep  8 12:27:06 2013 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sun Sep  8 12:27:06 2013 : Debug:     cache {
Sun Sep  8 12:27:06 2013 : Debug:     enable = no
Sun Sep  8 12:27:06 2013 : Debug:     lifetime = 24
Sun Sep  8 12:27:06 2013 : Debug:     max_entries = 255
Sun Sep  8 12:27:06 2013 : Debug:     }
Sun Sep  8 12:27:06 2013 : Debug:     verify {
Sun Sep  8 12:27:06 2013 : Debug:     }
Sun Sep  8 12:27:06 2013 : Debug:    }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-ttls
Sun Sep  8 12:27:06 2013 : Debug:    ttls {
Sun Sep  8 12:27:06 2013 : Debug:     default_eap_type = "md5"
Sun Sep  8 12:27:06 2013 : Debug:     copy_request_to_tunnel = no
Sun Sep  8 12:27:06 2013 : Debug:     use_tunneled_reply = no
Sun Sep  8 12:27:06 2013 : Debug:     virtual_server = "inner-tunnel"
Sun Sep  8 12:27:06 2013 : Debug:     include_length = yes
Sun Sep  8 12:27:06 2013 : Debug:    }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-peap
Sun Sep  8 12:27:06 2013 : Debug:    peap {
Sun Sep  8 12:27:06 2013 : Debug:     default_eap_type = "mschapv2"
Sun Sep  8 12:27:06 2013 : Debug:     copy_request_to_tunnel = no
Sun Sep  8 12:27:06 2013 : Debug:     use_tunneled_reply = no
Sun Sep  8 12:27:06 2013 : Debug:     proxy_tunneled_request_as_eap = yes
Sun Sep  8 12:27:06 2013 : Debug:     virtual_server = "inner-tunnel"
Sun Sep  8 12:27:06 2013 : Debug:    }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating eap-mschapv2
Sun Sep  8 12:27:06 2013 : Debug:    mschapv2 {
Sun Sep  8 12:27:06 2013 : Debug:     with_ntdomain_hack = no
Sun Sep  8 12:27:06 2013 : Debug:    }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_realm
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sun Sep  8 12:27:06 2013 : Debug:   realm suffix {
Sun Sep  8 12:27:06 2013 : Debug:     format = "suffix"
Sun Sep  8 12:27:06 2013 : Debug:     delimiter = "@"
Sun Sep  8 12:27:06 2013 : Debug:     ignore_default = no
Sun Sep  8 12:27:06 2013 : Debug:     ignore_null = no
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_files, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_files
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sun Sep  8 12:27:06 2013 : Debug:   files {
Sun Sep  8 12:27:06 2013 : Debug:     usersfile = "/etc/freeradius/users"
Sun Sep  8 12:27:06 2013 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sun Sep  8 12:27:06 2013 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sun Sep  8 12:27:06 2013 : Debug:     compat = "no"
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking session {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_radutmp
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sun Sep  8 12:27:06 2013 : Debug:   radutmp {
Sun Sep  8 12:27:06 2013 : Debug:     filename = "/var/log/freeradius/radutmp"
Sun Sep  8 12:27:06 2013 : Debug:     username = "%{User-Name}"
Sun Sep  8 12:27:06 2013 : Debug:     case_sensitive = yes
Sun Sep  8 12:27:06 2013 : Debug:     check_with_nas = yes
Sun Sep  8 12:27:06 2013 : Debug:     perm = 384
Sun Sep  8 12:27:06 2013 : Debug:     callerid = yes
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking post-auth {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_attr_filter
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module  "attr_filter.access_reject" from file  /etc/freeradius/modules/attr_filter
Sun Sep  8 12:27:06 2013 : Debug:   attr_filter attr_filter.access_reject {
Sun Sep  8 12:27:06 2013 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sun Sep  8 12:27:06 2013 : Debug:     key = "%{User-Name}"
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  } # modules
Sun Sep  8 12:27:06 2013 : Debug: } # server
Sun Sep  8 12:27:06 2013 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sun Sep  8 12:27:06 2013 : Debug:  modules {
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_digest
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_preprocess
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sun Sep  8 12:27:06 2013 : Debug:   preprocess {
Sun Sep  8 12:27:06 2013 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sun Sep  8 12:27:06 2013 : Debug:     hints = "/etc/freeradius/hints"
Sun Sep  8 12:27:06 2013 : Debug:     with_ascend_hack = no
Sun Sep  8 12:27:06 2013 : Debug:     ascend_channels_per_line = 23
Sun Sep  8 12:27:06 2013 : Debug:     with_ntdomain_hack = no
Sun Sep  8 12:27:06 2013 : Debug:     with_specialix_jetstream_hack = no
Sun Sep  8 12:27:06 2013 : Debug:     with_cisco_vsa_hack = no
Sun Sep  8 12:27:06 2013 : Debug:     with_alvarion_vsa_hack = no
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking preacct {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_acct_unique
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sun Sep  8 12:27:06 2013 : Debug:   acct_unique {
Sun Sep  8 12:27:06 2013 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking accounting {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sun Sep  8 12:27:06 2013 : Debug:  Module: Linked to module rlm_detail
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sun Sep  8 12:27:06 2013 : Debug:   detail {
Sun Sep  8 12:27:06 2013 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sun Sep  8 12:27:06 2013 : Debug:     header = "%t"
Sun Sep  8 12:27:06 2013 : Debug:     detailperm = 384
Sun Sep  8 12:27:06 2013 : Debug:     dirperm = 493
Sun Sep  8 12:27:06 2013 : Debug:     locking = no
Sun Sep  8 12:27:06 2013 : Debug:     log_packet_header = no
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Instantiating module  "attr_filter.accounting_response" from file  /etc/freeradius/modules/attr_filter
Sun Sep  8 12:27:06 2013 : Debug:   attr_filter attr_filter.accounting_response {
Sun Sep  8 12:27:06 2013 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sun Sep  8 12:27:06 2013 : Debug:     key = "%{User-Name}"
Sun Sep  8 12:27:06 2013 : Debug:   }
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking session {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:  Module: Checking post-auth {...} for more modules to load
Sun Sep  8 12:27:06 2013 : Debug:  } # modules
Sun Sep  8 12:27:06 2013 : Debug: } # server
Sun Sep  8 12:27:06 2013 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sun Sep  8 12:27:06 2013 : Debug: listen {
Sun Sep  8 12:27:06 2013 : Debug:     type = "auth"
Sun Sep  8 12:27:06 2013 : Debug:     ipaddr = *
Sun Sep  8 12:27:06 2013 : Debug:     port = 0
Sun Sep  8 12:27:06 2013 : Debug: }
Sun Sep  8 12:27:06 2013 : Debug: listen {
Sun Sep  8 12:27:06 2013 : Debug:     type = "acct"
Sun Sep  8 12:27:06 2013 : Debug:     ipaddr = *
Sun Sep  8 12:27:06 2013 : Debug:     port = 0
Sun Sep  8 12:27:06 2013 : Debug: }
Sun Sep  8 12:27:06 2013 : Debug: listen {
Sun Sep  8 12:27:06 2013 : Debug:     type = "auth"
Sun Sep  8 12:27:06 2013 : Debug:     ipaddr = 127.0.0.1
Sun Sep  8 12:27:06 2013 : Debug:     port = 18120
Sun Sep  8 12:27:06 2013 : Debug: }
Sun Sep  8 12:27:06 2013 : Debug: Listening on authentication address * port 1812
Sun Sep  8 12:27:06 2013 : Debug: Listening on accounting address * port 1813
Sun Sep  8 12:27:06 2013 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sun Sep  8 12:27:06 2013 : Debug: Listening on proxy address * port 1814
Sun Sep  8 12:27:06 2013 : Info: Ready to process requests.
```

This`s what i get after i run [COLOR=#ff0000]redtest [/COLOR]: 


[HTML]test@test:~$  sudo radtest "John Doe" hello 127.0.0.1 0 testing123
Sending Access-Request of id 164 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
Sending Access-Request of id 164 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
Sending Access-Request of id 164 to 127.0.0.1 port 1812
    User-Name = "John Doe"
    User-Password = "hello"
    NAS-IP-Address = 127.0.1.1
    NAS-Port = 0
radclient: no response from server for ID 164 socket 3

[/HTML]

---

### Post by laughmo on 2013-09-09
hi, 
thanks for sharing the freeradius folder.

firstly, the line for files is commented in your /etc/freeradius/site-available/default:
#  Read the 'users' file
#    files

it should be like this:
#  Read the 'users' file
    files


secondly, you do not have John Doe in your /etc/freeradius/users files;

[FONT=&amp]"John Doe"     Auth-Type := Local, User-Password == "hello"[/FONT]
  [FONT=&amp]               Reply-Message = "Hello, %u"

what you have is:[/FONT]

"Anggi Shahlan"    Cleartext-Password := "liquid"
        Reply-Message = "Oke sip, %{User-Name}"

so the test should be:

sudo radtest "Anggi Shahlan" hello 127.0.0.1 0 testing123

---

### Post by zQKsFFT on 2013-09-13
When I try to log on to DaloRADIUS, /daloradius/dologin.php - the page is all blank...
Any idea?

---

### Post by yvongosselin on 2013-10-25
hello

i have problem with freeradius

after freeradius -XXX

i have this error

Error: rlm_sqlcounter: No such attribute ChilliSpot_Max_Total_Octets
Error: /etc/freeradius/sql/mysql/counter.conf [130]: Instantiation failed for module ''chillispot_max_bytes''

need help please

---

### Post by okay7675 on 2013-10-27
Hi,

Thanks for your instructions, everything is working until i get to the "daloradius Quick start", i cannot access the daloradius webmanagement page. I have KOHA installed on the same serverand it uses localhost/192.168.2.2 (local ip of my server), so i think there's a conflict between the two. May you please guide me on how to fix this?

---

### Post by okay7675 on 2013-10-28
I figured it out!I added the following to /etc/apache2/sites-enabled/library file 

 Listen 9999
 NameVirtualHost *:9999

<VirtualHost *:9999>
ServerName 127.0.0.1
DocumentRoot /var/www/daloradius
</VirtualHost>

So now i can access Koha on ports 80 and 8080, and daloradius on port 9999! Reading the apache virtual hosts docs was helpful - [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

I'm using ubuntu 12.04 LTS by the way

---

### Post by desirebazaanah on 2013-12-03
pls can i get images to this effect so i can also do this on my ubuntu 12 server...
am still new to this linux stuff and seriously need your help thanx...you can even send it to me by mail.....desirebazaanah@gmail.com
stay blessed boss..

---

### Post by ahmad7jafari on 2014-01-12
hi 
I am use daloradius virtualbox image that run under ubuntu 10.4 LTS and install coova-chilli .
all is good But client have any redirect to login page!
there is my output of chilli debug:
```
root@lamp ~# chilli --fg --debug
main-opt.c: 403: 0 (Debug) DHCP Listen: 192.168.10.208
main-opt.c: 404: 0 (Debug) UAM Listen: 192.168.10.208
garden.c: 62: 0 (Debug) Uamallowed www.coova.org
garden.c: 126: 0 (Debug) Invalid uamallowed domain or address: www.coova.org!
garden.c: 62: 0 (Debug) Uamallowed 192.168.10.208
garden.c: 44: 0 (Debug) Uamallowed IP address #0:512: proto=0 host=192.168.10.208 port=0
garden.c: 62: 0 (Debug) Uamallowed
garden.c: 126: 0 (Debug) Invalid uamallowed domain or address: !
garden.c: 62: 0 (Debug) Uamallowed www.coova.org
garden.c: 126: 0 (Debug) Invalid uamallowed domain or address: www.coova.org!
garden.c: 62: 0 (Debug) Uamallowed 192.168.10.1/255
options.c: 57: 0 (Debug) Invalid mask
garden.c: 115: 0 (Debug) Invalid uamallowed network address or mask 192.168.10.1/255!
options.c: 367: 0 (Debug) PID 1568 saving options to /var/run/chilli.1567.cfg.bin
options.c: 544: 0 (Debug) PID 1567 reloaded binary options file
chilli.c: 4848: 0 (Debug) clock realtime sec 1389509098 nsec 962522139
chilli.c: 4853: 0 (Debug) clock monotonic sec 325 nsec 654157486
tun.c: 520: 0 (Debug) TX queue length set to 100
ippool.c: 322: 0 (Debug) Hashlog 8 253 256

net.c: 1028: 0 (Debug) Net SNDBUF 112640
net.c: 1031: 0 (Debug) Net RCVBUF 112640
net.c: 1083: 0 (Debug) device eth1 ifindex 3
dhcp.c: 208: 0 (Debug) GARP: Replying to broadcast
chilli.c: 5084: 0 (Debug) Waiting for client request...
radius.c: 1423: 0 (Debug) RADIUS to 127.0.0.1:1813
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=08:00:27:50:7f:13 dst=00:11:09:5e:2f:c9 prot=0800 2048 len=234
dhcp.c: 2795: 0 (Debug) Not for our MAC or broadcast: 00-11-09-5E-2F-C9
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=08:00:27:50:7f:13 prot=0800 2048 len=60
dhcp.c: 2795: 0 (Debug) Not for our MAC or broadcast: 08-00-27-50-7F-13
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=08:00:27:50:7f:13 dst=00:11:09:5e:2f:c9 prot=0800 2048 len=106
dhcp.c: 2795: 0 (Debug) Not for our MAC or broadcast: 00-11-09-5E-2F-C9
main-script.c: 75: 0 (Debug) USER root(0/0), GROUP root(0/0) CHILLI[UID 108, GID 112]
main-script.c: 93: 0 (Debug) Running /etc/chilli/up.sh (0/0)
/etc/chilli/up.sh: 64: ./etc/chilli/ipup.sh: not found
chilli.c: 273: 0 (Debug) caught 17 via selfpipe
chilli.c: 232: 0 (Debug) child 1570 terminated
.
.
.
.
.
.
.

dns.c: 182: 0 (Debug) dns_copy_res(left=20 olen=20 qsize=512)
dns.c: 205: 0 (Debug) It was a dns record type: 1 class: 1
dns.c: 39: 0 (Debug) dlen=512 reslen=20 olen=20 lvl=0
dns.c: 73: 0 (Debug) part[www] reslen=19 l=3 dlen=512
dns.c: 73: 0 (Debug) part[google] reslen=15 l=6 dlen=508
dns.c: 73: 0 (Debug) part[com] reslen=8 l=3 dlen=501
dns.c: 234: 0 (Debug) Q: www.google.com
dhcp.c: 1411: 0 (Debug) an: 0
dhcp.c: 1412: 0 (Debug) ns: 0
dhcp.c: 1413: 0 (Debug) ar: 0
dhcp.c: 1415: 0 (Debug) left (should be zero): 0
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=08:00:27:bf:cc:9a prot=0800 2048 len=74
dhcp.c: 1385: 0 (Debug) dhcp_dns plen=74 dlen=20 olen=20
dhcp.c: 1387: 0 (Debug) DNS ID:    31921
dhcp.c: 1388: 0 (Debug) DNS Flags: 256
dhcp.c: 1410: 0 (Debug) qd: 1
dns.c: 182: 0 (Debug) dns_copy_res(left=20 olen=20 qsize=512)
dns.c: 205: 0 (Debug) It was a dns record type: 1 class: 1
dns.c: 39: 0 (Debug) dlen=512 reslen=20 olen=20 lvl=0
dns.c: 73: 0 (Debug) part[www] reslen=19 l=3 dlen=512
dns.c: 73: 0 (Debug) part[google] reslen=15 l=6 dlen=508
dns.c: 73: 0 (Debug) part[com] reslen=8 l=3 dlen=501
dns.c: 234: 0 (Debug) Q: www.google.com
dhcp.c: 1411: 0 (Debug) an: 0
dhcp.c: 1412: 0 (Debug) ns: 0
dhcp.c: 1413: 0 (Debug) ar: 0
dhcp.c: 1415: 0 (Debug) left (should be zero): 0
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=ff:ff:ff:ff:ff:ff prot=0800 2048 len=92
dhcp.c: 2890: 0 (Debug) Broadcasted UDP to port 137
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=ff:ff:ff:ff:ff:ff prot=0800 2048 len=92
dhcp.c: 2890: 0 (Debug) Broadcasted UDP to port 137
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=ff:ff:ff:ff:ff:ff prot=0800 2048 len=92
dhcp.c: 2890: 0 (Debug) Broadcasted UDP to port 137


```
where:
192.168.10.208 is my lan NIC
192.168.10.206 is my internet NIC
and client winXP get ip:192.168.10.1 from serevr

please help me ......

---

### Post by okay7675 on 2014-01-25
Hi laughmo,

I have the freeradius server up and running, but all my attempts at a client login are being rejected with the error* username and/or passowrd (sic) was not valid*.

I ran freeradius in debug mode and tried to connect, first as a member  user (username lennon) and then as a batch user (username omniWezkHeWq).  The results are in the attached file debug.txt

```

root@ubuntu:~# /etc/init.d/freeradius stop
 * Stopping FreeRADIUS daemon freeradius                                 [ OK ] 
root@ubuntu:~#  freeradius -XXX
Sat Jan 25 20:14:02 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sat Jan 25 20:14:02 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sat Jan 25 20:14:02 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sat Jan 25 20:14:02 2014 : Info: PARTICULAR PURPOSE. 
Sat Jan 25 20:14:02 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sat Jan 25 20:14:02 2014 : Info: GNU General Public License v2. 
Sat Jan 25 20:14:02 2014 : Info: Starting - reading configuration files ...
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sat Jan 25 20:14:02 2014 : Debug: including files in directory /etc/freeradius/modules/
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sat Jan 25 20:14:02 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:14:02 2014 : Debug: main {
Sat Jan 25 20:14:02 2014 : Debug:     user = "freerad"
Sat Jan 25 20:14:02 2014 : Debug:     group = "freerad"
Sat Jan 25 20:14:02 2014 : Debug:     allow_core_dumps = no
Sat Jan 25 20:14:02 2014 : Debug: }
Sat Jan 25 20:14:02 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sat Jan 25 20:14:03 2014 : Debug: main {
Sat Jan 25 20:14:03 2014 : Debug:     prefix = "/usr"
Sat Jan 25 20:14:03 2014 : Debug:     localstatedir = "/var"
Sat Jan 25 20:14:03 2014 : Debug:     logdir = "/var/log/freeradius"
Sat Jan 25 20:14:03 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sat Jan 25 20:14:03 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sat Jan 25 20:14:03 2014 : Debug:     hostname_lookups = no
Sat Jan 25 20:14:03 2014 : Debug:     max_request_time = 30
Sat Jan 25 20:14:03 2014 : Debug:     cleanup_delay = 5
Sat Jan 25 20:14:03 2014 : Debug:     max_requests = 1024
Sat Jan 25 20:14:03 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sat Jan 25 20:14:03 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sat Jan 25 20:14:03 2014 : Debug:     debug_level = 0
Sat Jan 25 20:14:03 2014 : Debug:     proxy_requests = yes
Sat Jan 25 20:14:03 2014 : Debug:  log {
Sat Jan 25 20:14:03 2014 : Debug:     stripped_names = no
Sat Jan 25 20:14:03 2014 : Debug:     auth = no
Sat Jan 25 20:14:03 2014 : Debug:     auth_badpass = no
Sat Jan 25 20:14:03 2014 : Debug:     auth_goodpass = no
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  security {
Sat Jan 25 20:14:03 2014 : Debug:     max_attributes = 200
Sat Jan 25 20:14:03 2014 : Debug:     reject_delay = 1
Sat Jan 25 20:14:03 2014 : Debug:     status_server = yes
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sat Jan 25 20:14:03 2014 : Debug:  proxy server {
Sat Jan 25 20:14:03 2014 : Debug:     retry_delay = 5
Sat Jan 25 20:14:03 2014 : Debug:     retry_count = 3
Sat Jan 25 20:14:03 2014 : Debug:     default_fallback = no
Sat Jan 25 20:14:03 2014 : Debug:     dead_time = 120
Sat Jan 25 20:14:03 2014 : Debug:     wake_all_if_all_dead = no
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  home_server localhost {
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:14:03 2014 : Debug:     port = 1812
Sat Jan 25 20:14:03 2014 : Debug:     type = "auth"
Sat Jan 25 20:14:03 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:14:03 2014 : Debug:     response_window = 20
Sat Jan 25 20:14:03 2014 : Debug:     max_outstanding = 65536
Sat Jan 25 20:14:03 2014 : Debug:     require_message_authenticator = yes
Sat Jan 25 20:14:03 2014 : Debug:     zombie_period = 40
Sat Jan 25 20:14:03 2014 : Debug:     status_check = "status-server"
Sat Jan 25 20:14:03 2014 : Debug:     ping_interval = 30
Sat Jan 25 20:14:03 2014 : Debug:     check_interval = 30
Sat Jan 25 20:14:03 2014 : Debug:     num_answers_to_alive = 3
Sat Jan 25 20:14:03 2014 : Debug:     num_pings_to_alive = 3
Sat Jan 25 20:14:03 2014 : Debug:     revive_interval = 120
Sat Jan 25 20:14:03 2014 : Debug:     status_check_timeout = 4
Sat Jan 25 20:14:03 2014 : Debug:     irt = 2
Sat Jan 25 20:14:03 2014 : Debug:     mrt = 16
Sat Jan 25 20:14:03 2014 : Debug:     mrc = 5
Sat Jan 25 20:14:03 2014 : Debug:     mrd = 30
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  home_server_pool my_auth_failover {
Sat Jan 25 20:14:03 2014 : Debug:     type = fail-over
Sat Jan 25 20:14:03 2014 : Debug:     home_server = localhost
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  realm example.com {
Sat Jan 25 20:14:03 2014 : Debug:     auth_pool = my_auth_failover
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  realm LOCAL {
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Loading Clients ####
Sat Jan 25 20:14:03 2014 : Debug:  client localhost {
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:14:03 2014 : Debug:     require_message_authenticator = no
Sat Jan 25 20:14:03 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:14:03 2014 : Debug:     nastype = "other"
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Instantiating modules ####
Sat Jan 25 20:14:03 2014 : Debug:  instantiate {
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_exec
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sat Jan 25 20:14:03 2014 : Debug:   exec {
Sat Jan 25 20:14:03 2014 : Debug:     wait = no
Sat Jan 25 20:14:03 2014 : Debug:     input_pairs = "request"
Sat Jan 25 20:14:03 2014 : Debug:     shell_escape = yes
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:14:03 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sat Jan 25 20:14:03 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:14:03 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:14:03 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:14:03 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:14:03 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:14:03 2014 : Debug:     query = "SELECT  SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE  UserName='%{%k}'"
Sat Jan 25 20:14:03 2014 : Debug:     reset = "never"
Sat Jan 25 20:14:03 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:14:03 2014 : Debug:   sqlcounter noresetcounter {
Sat Jan 25 20:14:03 2014 : Debug:     counter-name = "Session-Timeout"
Sat Jan 25 20:14:03 2014 : Debug:     check-name = "Session-Timeout"
Sat Jan 25 20:14:03 2014 : Debug:     reply-name = "Session-Timeout"
Sat Jan 25 20:14:03 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:14:03 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:14:03 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 20:14:03 2014 : Debug:     reset = "never"
Sat Jan 25 20:14:03 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_expr
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_expiration
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sat Jan 25 20:14:03 2014 : Debug:   expiration {
Sat Jan 25 20:14:03 2014 : Debug:     reply-message = "Password Has Expired  "
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_logintime
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sat Jan 25 20:14:03 2014 : Debug:   logintime {
Sat Jan 25 20:14:03 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sat Jan 25 20:14:03 2014 : Debug:     minimum-timeout = 60
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sat Jan 25 20:14:03 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:14:03 2014 : Debug:  modules {
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_pap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sat Jan 25 20:14:03 2014 : Debug:   pap {
Sat Jan 25 20:14:03 2014 : Debug:     encryption_scheme = "auto"
Sat Jan 25 20:14:03 2014 : Debug:     auto_header = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_chap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_mschap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sat Jan 25 20:14:03 2014 : Debug:   mschap {
Sat Jan 25 20:14:03 2014 : Debug:     use_mppe = yes
Sat Jan 25 20:14:03 2014 : Debug:     require_encryption = no
Sat Jan 25 20:14:03 2014 : Debug:     require_strong = no
Sat Jan 25 20:14:03 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_unix
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sat Jan 25 20:14:03 2014 : Debug:   unix {
Sat Jan 25 20:14:03 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_eap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sat Jan 25 20:14:03 2014 : Debug:   eap {
Sat Jan 25 20:14:03 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:14:03 2014 : Debug:     timer_expire = 60
Sat Jan 25 20:14:03 2014 : Debug:     ignore_unknown_eap_types = no
Sat Jan 25 20:14:03 2014 : Debug:     cisco_accounting_username_bug = no
Sat Jan 25 20:14:03 2014 : Debug:     max_sessions = 4096
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-md5
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-leap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-gtc
Sat Jan 25 20:14:03 2014 : Debug:    gtc {
Sat Jan 25 20:14:03 2014 : Debug:     challenge = "Password: "
Sat Jan 25 20:14:03 2014 : Debug:     auth_type = "PAP"
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-tls
Sat Jan 25 20:14:03 2014 : Debug:    tls {
Sat Jan 25 20:14:03 2014 : Debug:     rsa_key_exchange = no
Sat Jan 25 20:14:03 2014 : Debug:     dh_key_exchange = yes
Sat Jan 25 20:14:03 2014 : Debug:     rsa_key_length = 512
Sat Jan 25 20:14:03 2014 : Debug:     dh_key_length = 512
Sat Jan 25 20:14:03 2014 : Debug:     verify_depth = 0
Sat Jan 25 20:14:03 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sat Jan 25 20:14:03 2014 : Debug:     pem_file_type = yes
Sat Jan 25 20:14:03 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sat Jan 25 20:14:03 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sat Jan 25 20:14:03 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sat Jan 25 20:14:03 2014 : Debug:     private_key_password = "whatever"
Sat Jan 25 20:14:03 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sat Jan 25 20:14:03 2014 : Debug:     random_file = "/dev/urandom"
Sat Jan 25 20:14:03 2014 : Debug:     fragment_size = 1024
Sat Jan 25 20:14:03 2014 : Debug:     include_length = yes
Sat Jan 25 20:14:03 2014 : Debug:     check_crl = no
Sat Jan 25 20:14:03 2014 : Debug:     cipher_list = "DEFAULT"
Sat Jan 25 20:14:03 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sat Jan 25 20:14:03 2014 : Debug:     cache {
Sat Jan 25 20:14:03 2014 : Debug:     enable = no
Sat Jan 25 20:14:03 2014 : Debug:     lifetime = 24
Sat Jan 25 20:14:03 2014 : Debug:     max_entries = 255
Sat Jan 25 20:14:03 2014 : Debug:     }
Sat Jan 25 20:14:03 2014 : Debug:     verify {
Sat Jan 25 20:14:03 2014 : Debug:     }
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-ttls
Sat Jan 25 20:14:03 2014 : Debug:    ttls {
Sat Jan 25 20:14:03 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:14:03 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:14:03 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:14:03 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:14:03 2014 : Debug:     include_length = yes
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-peap
Sat Jan 25 20:14:03 2014 : Debug:    peap {
Sat Jan 25 20:14:03 2014 : Debug:     default_eap_type = "mschapv2"
Sat Jan 25 20:14:03 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:14:03 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:14:03 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sat Jan 25 20:14:03 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-mschapv2
Sat Jan 25 20:14:03 2014 : Debug:    mschapv2 {
Sat Jan 25 20:14:03 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_realm
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sat Jan 25 20:14:03 2014 : Debug:   realm suffix {
Sat Jan 25 20:14:03 2014 : Debug:     format = "suffix"
Sat Jan 25 20:14:03 2014 : Debug:     delimiter = "@"
Sat Jan 25 20:14:03 2014 : Debug:     ignore_default = no
Sat Jan 25 20:14:03 2014 : Debug:     ignore_null = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_files
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sat Jan 25 20:14:03 2014 : Debug:   files {
Sat Jan 25 20:14:03 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sat Jan 25 20:14:03 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sat Jan 25 20:14:03 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sat Jan 25 20:14:03 2014 : Debug:     compat = "no"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_radutmp
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sat Jan 25 20:14:03 2014 : Debug:   radutmp {
Sat Jan 25 20:14:03 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sat Jan 25 20:14:03 2014 : Debug:     username = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:     case_sensitive = yes
Sat Jan 25 20:14:03 2014 : Debug:     check_with_nas = yes
Sat Jan 25 20:14:03 2014 : Debug:     perm = 384
Sat Jan 25 20:14:03 2014 : Debug:     callerid = yes
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "attr_filter.access_reject" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:14:03 2014 : Debug:   attr_filter attr_filter.access_reject {
Sat Jan 25 20:14:03 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sat Jan 25 20:14:03 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  } # modules
Sat Jan 25 20:14:03 2014 : Debug: } # server
Sat Jan 25 20:14:03 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sat Jan 25 20:14:03 2014 : Debug:  modules {
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_digest
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_preprocess
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sat Jan 25 20:14:03 2014 : Debug:   preprocess {
Sat Jan 25 20:14:03 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sat Jan 25 20:14:03 2014 : Debug:     hints = "/etc/freeradius/hints"
Sat Jan 25 20:14:03 2014 : Debug:     with_ascend_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     ascend_channels_per_line = 23
Sat Jan 25 20:14:03 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     with_specialix_jetstream_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     with_cisco_vsa_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     with_alvarion_vsa_hack = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_sql
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sat Jan 25 20:14:03 2014 : Debug:   sql {
Sat Jan 25 20:14:03 2014 : Debug:     driver = "rlm_sql_mysql"
Sat Jan 25 20:14:03 2014 : Debug:     server = "localhost"
Sat Jan 25 20:14:03 2014 : Debug:     port = ""
Sat Jan 25 20:14:03 2014 : Debug:     login = "radius"
Sat Jan 25 20:14:03 2014 : Debug:     password = "radpass"
Sat Jan 25 20:14:03 2014 : Debug:     radius_db = "radius"
Sat Jan 25 20:14:03 2014 : Debug:     read_groups = yes
Sat Jan 25 20:14:03 2014 : Debug:     sqltrace = no
Sat Jan 25 20:14:03 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sat Jan 25 20:14:03 2014 : Debug:     readclients = no
Sat Jan 25 20:14:03 2014 : Debug:     deletestalesessions = yes
Sat Jan 25 20:14:03 2014 : Debug:     num_sql_socks = 5
Sat Jan 25 20:14:03 2014 : Debug:     lifetime = 0
Sat Jan 25 20:14:03 2014 : Debug:     max_queries = 0
Sat Jan 25 20:14:03 2014 : Debug:     sql_user_name = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:     default_user_profile = ""
Sat Jan 25 20:14:03 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_check_query = "SELECT  id, username, attribute, value, op           FROM radcheck            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_reply_query = "SELECT  id, username, attribute, value, op           FROM radreply            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_group_check_query =  "SELECT id, groupname, attribute,           Value, op           FROM  radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_group_reply_query =  "SELECT id, groupname, attribute,           value, op           FROM  radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_onoff_query = "           UPDATE radacct           SET              acctstoptime       =  '%S',               acctsessiontime    =  unix_timestamp('%S') -                                     unix_timestamp(acctstarttime),               acctterminatecause =  '%{Acct-Terminate-Cause}',               acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE  acctstoptime IS NULL           AND nasipaddress      =   '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_update_query = "            UPDATE radacct           SET              framedipaddress =  '%{Framed-IP-Address}',              acctsessiontime     =  '%{Acct-Session-Time}',              acctinputoctets     =  '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                     '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets     = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                     '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username        =  '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_update_query_alt = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,       username,              realm,            nasipaddress,       nasportid,              nasporttype,      acctstarttime,      acctsessiontime,              acctauthentic,    connectinfo_start,  acctinputoctets,              acctoutputoctets, calledstationid,    callingstationid,              servicetype,      framedprotocol,     framedipaddress,              acctstartdelay,   xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                        INTERVAL (%{%{Acct-Session-Time}:-0} +                                  %{%{Acct-Delay-Time}:-0}) SECOND),                        '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',               '%{%{Acct-Input-Gigawords}:-0}' << 32 |               '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Service-Type}',  '%{Framed-Protocol}',              '%{Framed-IP-Address}',               '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_start_query = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,     nasportid,               nasporttype,      acctstarttime,    acctstoptime,               acctsessiontime,  acctauthentic,    connectinfo_start,               connectinfo_stop, acctinputoctets,  acctoutputoctets,               calledstationid,  callingstationid, acctterminatecause,               servicetype,      framedprotocol,   framedipaddress,               acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',               '%{SQL-User-Name}',              '%{Realm}',  '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',  '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',               '', '0', '0',              '%{Called-Station-Id}',  '%{Calling-Station-Id}', '',              '%{Service-Type}',  '%{Framed-Protocol}', '%{Framed-IP-Address}',               '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_start_query_alt = "            UPDATE radacct SET              acctstarttime     = '%S',               acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',               connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  =  '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'            AND nasipaddress     = '%{NAS-IP-Address}'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_stop_query = "            UPDATE radacct SET              acctstoptime       = '%S',               acctsessiontime    = '%{Acct-Session-Time}',               acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Input-Octets}:-0}',               acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}',               acctterminatecause = '%{Acct-Terminate-Cause}',               acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',               connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   =  '%{Acct-Session-Id}'           AND username          =  '%{SQL-User-Name}'           AND nasipaddress      =  '%{NAS-IP-Address}'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_stop_query_alt = "            INSERT INTO radacct             (acctsessionid, acctuniqueid,  username,              realm, nasipaddress, nasportid,               nasporttype, acctstarttime, acctstoptime,              acctsessiontime,  acctauthentic, connectinfo_start,              connectinfo_stop,  acctinputoctets, acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,  framedprotocol, framedipaddress,              acctstartdelay,  acctstopdelay)           VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                   INTERVAL (%{%{Acct-Session-Time}:-0} +                   %{%{Acct-Delay-Time}:-0}) SECOND),              '%S',  '%{Acct-Session-Time}', '%{Acct-Authentic}', '',               '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' <<  32 |              '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',               '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',               '0', '%{%{Acct-Delay-Time}:-0}')"
Sat Jan 25 20:14:03 2014 : Debug:     group_membership_query = "SELECT  groupname           FROM radusergroup           WHERE username =  '%{SQL-User-Name}'           ORDER BY priority"
Sat Jan 25 20:14:03 2014 : Debug:     connect_failure_retry_delay = 60
Sat Jan 25 20:14:03 2014 : Debug:     simul_count_query = ""
Sat Jan 25 20:14:03 2014 : Debug:     simul_verify_query = "SELECT  radacctid, acctsessionid, username,                                 nasipaddress, nasportid, framedipaddress,                                 callingstationid, framedprotocol                                FROM  radacct                                WHERE username =  '%{SQL-User-Name}'                                AND acctstoptime IS  NULL"
Sat Jan 25 20:14:03 2014 : Debug:     postauth_query = "INSERT INTO  radpostauth                           (username, pass, reply, authdate)                            VALUES (                            '%{User-Name}',                            '%{%{User-Password}:-%{Chap-Password}}',                            '%{reply:razz:acket-Type}', '%S')"
Sat Jan 25 20:14:03 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 20:14:03 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 20:14:03 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 20:14:03 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 20:14:03 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:14:03 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:14:03 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): Failed to connect to any SQL server.
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:14:03 2014 : Debug:   acct_unique {
Sat Jan 25 20:14:03 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_detail
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sat Jan 25 20:14:03 2014 : Debug:   detail {
Sat Jan 25 20:14:03 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sat Jan 25 20:14:03 2014 : Debug:     header = "%t"
Sat Jan 25 20:14:03 2014 : Debug:     detailperm = 384
Sat Jan 25 20:14:03 2014 : Debug:     dirperm = 493
Sat Jan 25 20:14:03 2014 : Debug:     locking = no
Sat Jan 25 20:14:03 2014 : Debug:     log_packet_header = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "attr_filter.accounting_response" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:14:03 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sat Jan 25 20:14:03 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sat Jan 25 20:14:03 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  } # modules
Sat Jan 25 20:14:03 2014 : Debug: } # server
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sat Jan 25 20:14:03 2014 : Debug: listen {
Sat Jan 25 20:14:03 2014 : Debug:     type = "auth"
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = *
Sat Jan 25 20:14:03 2014 : Debug:     port = 0
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: listen {
Sat Jan 25 20:14:03 2014 : Debug:     type = "acct"
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = *
Sat Jan 25 20:14:03 2014 : Debug:     port = 0
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: listen {
Sat Jan 25 20:14:03 2014 : Debug:     type = "auth"
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:14:03 2014 : Debug:     port = 18120
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: Listening on authentication address * port 1812
Sat Jan 25 20:14:03 2014 : Debug: Listening on accounting address * port 1813
Sat Jan 25 20:14:03 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sat Jan 25 20:14:03 2014 : Debug: Listening on proxy address * port 1814
Sat Jan 25 20:14:03 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 40294, id=116, length=289
    ChilliSpot-Version = "1.2.9"
    User-Name = "lennon"
    CHAP-Challenge = 0xd837ab6ba881992c454c811ef30d8d1f
    CHAP-Password = 0x00bfacbbd38f831e6c26aef87a71350efd
    Service-Type = Login-User
    Acct-Session-Id = "52e3f80800000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x1a7d60176ce601b1aa9216e2c15b662b
Sat Jan 25 20:14:09 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:14:09 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:14:09 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:14:09 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:14:09 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:14:09 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:14:09 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:14:09 2014 : Info: [suffix] No '@' in User-Name = "lennon", looking up realm NULL
Sat Jan 25 20:14:09 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:14:09 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:14:09 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:14:09 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:14:09 2014 : Info: [sql]     expand: %{User-Name} -> lennon
Sat Jan 25 20:14:09 2014 : Info: [sql] sql_set_user escaped user --> 'lennon'
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:14:09 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:14:09 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:14:09 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:14:09 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:14:09 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:14:09 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> lennon
Sat Jan 25 20:14:09 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:14:09 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:14:09 2014 : Info: Delaying reject of request 0 for 1 seconds
Sat Jan 25 20:14:09 2014 : Debug: Going to the next request
Sat Jan 25 20:14:09 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:14:10 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 116 to 127.0.0.1 port 40294
Sat Jan 25 20:14:10 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:14:15 2014 : Info: Cleaning up request 0 ID 116 with timestamp +6
Sat Jan 25 20:14:15 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 41071, id=131, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0xb1d31df75780c9a095f3fe4d253860e4
    CHAP-Password = 0x00fc4cb7a9a433cccb18d0a3bcd8157449
    Service-Type = Login-User
    Acct-Session-Id = "52e3fef200000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x40328b5cd3fada0c2342ef5a7162736a
Sat Jan 25 20:20:24 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:20:24 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:20:24 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:20:24 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:20:24 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:20:24 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:20:24 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:20:24 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:20:24 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:20:24 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:20:24 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:20:24 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:20:24 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:20:24 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:20:24 2014 : Info: rlm_sql (sql): Trying to (re)connect unconnected handle 4..
Sat Jan 25 20:20:24 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 20:20:24 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 20:20:24 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:20:24 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:20:24 2014 : Error: rlm_sql (sql): Failed to connect DB handle #4
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:20:24 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 1
Sat Jan 25 20:20:24 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:20:24 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:20:24 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:20:24 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:20:24 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:20:24 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:20:24 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:20:24 2014 : Info: Delaying reject of request 1 for 1 seconds
Sat Jan 25 20:20:24 2014 : Debug: Going to the next request
Sat Jan 25 20:20:24 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:20:25 2014 : Info: Sending delayed reject for request 1
Sending Access-Reject of id 131 to 127.0.0.1 port 41071
Sat Jan 25 20:20:25 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:20:30 2014 : Info: Cleaning up request 1 ID 131 with timestamp +381
Sat Jan 25 20:20:30 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 60503, id=138, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0xff74f6e4b14087b180e55e8306e3e632
    CHAP-Password = 0x00f653d2c9d713a0854114d69d1ea166f8
    Service-Type = Login-User
    Acct-Session-Id = "52e4006900000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xbe5f9af59a3ffda37ad836e3b44dacd9
Sat Jan 25 20:21:29 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:29 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:21:29 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:21:29 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:21:29 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:21:29 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:21:29 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:21:29 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:21:29 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:21:29 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:21:29 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:21:29 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:21:29 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:29 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:21:29 2014 : Info: rlm_sql (sql): Trying to (re)connect unconnected handle 4..
Sat Jan 25 20:21:29 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 20:21:29 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 20:21:29 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:21:29 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:21:29 2014 : Error: rlm_sql (sql): Failed to connect DB handle #4
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:21:29 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 1
Sat Jan 25 20:21:29 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:21:29 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:21:29 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:29 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:21:29 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:29 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:21:29 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:21:29 2014 : Info: Delaying reject of request 2 for 1 seconds
Sat Jan 25 20:21:29 2014 : Debug: Going to the next request
Sat Jan 25 20:21:29 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:21:30 2014 : Info: Sending delayed reject for request 2
Sending Access-Reject of id 138 to 127.0.0.1 port 60503
Sat Jan 25 20:21:30 2014 : Debug: Waking up in 4.9 seconds.
rad_recv: Access-Request packet from host 127.0.0.1 port 37727, id=142, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0x3623bc4ba66d7d5b48d185158fb0b8fb
    CHAP-Password = 0x0005221589b8b7f85d79a2b774f62f6657
    Service-Type = Login-User
    Acct-Session-Id = "52e400aa00000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xb2649e5fca7e2612485ada443a70d46c
Sat Jan 25 20:21:33 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:33 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:21:33 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:21:33 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:21:33 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:21:33 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:21:33 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:21:33 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:21:33 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:21:33 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:21:33 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:21:33 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:21:33 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:33 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:21:33 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:21:33 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:21:33 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:21:33 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:33 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:21:33 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:33 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:21:33 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:21:33 2014 : Info: Delaying reject of request 3 for 1 seconds
Sat Jan 25 20:21:33 2014 : Debug: Going to the next request
Sat Jan 25 20:21:33 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:21:34 2014 : Info: Sending delayed reject for request 3
Sending Access-Reject of id 142 to 127.0.0.1 port 37727
Sat Jan 25 20:21:34 2014 : Debug: Waking up in 1.0 seconds.
Sat Jan 25 20:21:35 2014 : Info: Cleaning up request 2 ID 138 with timestamp +446
Sat Jan 25 20:21:35 2014 : Debug: Waking up in 3.9 seconds.
Sat Jan 25 20:21:39 2014 : Info: Cleaning up request 3 ID 142 with timestamp +450
Sat Jan 25 20:21:39 2014 : Info: Ready to process requests.
^C
root@ubuntu:~# clear

root@ubuntu:~# freeradisu -XXX
No command 'freeradisu' found, did you mean:
 Command 'freeradius' from package 'freeradius' (main)
freeradisu: command not found
root@ubuntu:~# freeradius -XXX
Sat Jan 25 20:21:59 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sat Jan 25 20:21:59 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sat Jan 25 20:21:59 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sat Jan 25 20:21:59 2014 : Info: PARTICULAR PURPOSE. 
Sat Jan 25 20:21:59 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sat Jan 25 20:21:59 2014 : Info: GNU General Public License v2. 
Sat Jan 25 20:21:59 2014 : Info: Starting - reading configuration files ...
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sat Jan 25 20:21:59 2014 : Debug: including files in directory /etc/freeradius/modules/
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sat Jan 25 20:21:59 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:21:59 2014 : Debug: main {
Sat Jan 25 20:21:59 2014 : Debug:     user = "freerad"
Sat Jan 25 20:21:59 2014 : Debug:     group = "freerad"
Sat Jan 25 20:21:59 2014 : Debug:     allow_core_dumps = no
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sat Jan 25 20:21:59 2014 : Debug: main {
Sat Jan 25 20:21:59 2014 : Debug:     prefix = "/usr"
Sat Jan 25 20:21:59 2014 : Debug:     localstatedir = "/var"
Sat Jan 25 20:21:59 2014 : Debug:     logdir = "/var/log/freeradius"
Sat Jan 25 20:21:59 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sat Jan 25 20:21:59 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sat Jan 25 20:21:59 2014 : Debug:     hostname_lookups = no
Sat Jan 25 20:21:59 2014 : Debug:     max_request_time = 30
Sat Jan 25 20:21:59 2014 : Debug:     cleanup_delay = 5
Sat Jan 25 20:21:59 2014 : Debug:     max_requests = 1024
Sat Jan 25 20:21:59 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sat Jan 25 20:21:59 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sat Jan 25 20:21:59 2014 : Debug:     debug_level = 0
Sat Jan 25 20:21:59 2014 : Debug:     proxy_requests = yes
Sat Jan 25 20:21:59 2014 : Debug:  log {
Sat Jan 25 20:21:59 2014 : Debug:     stripped_names = no
Sat Jan 25 20:21:59 2014 : Debug:     auth = no
Sat Jan 25 20:21:59 2014 : Debug:     auth_badpass = no
Sat Jan 25 20:21:59 2014 : Debug:     auth_goodpass = no
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  security {
Sat Jan 25 20:21:59 2014 : Debug:     max_attributes = 200
Sat Jan 25 20:21:59 2014 : Debug:     reject_delay = 1
Sat Jan 25 20:21:59 2014 : Debug:     status_server = yes
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sat Jan 25 20:21:59 2014 : Debug:  proxy server {
Sat Jan 25 20:21:59 2014 : Debug:     retry_delay = 5
Sat Jan 25 20:21:59 2014 : Debug:     retry_count = 3
Sat Jan 25 20:21:59 2014 : Debug:     default_fallback = no
Sat Jan 25 20:21:59 2014 : Debug:     dead_time = 120
Sat Jan 25 20:21:59 2014 : Debug:     wake_all_if_all_dead = no
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  home_server localhost {
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:21:59 2014 : Debug:     port = 1812
Sat Jan 25 20:21:59 2014 : Debug:     type = "auth"
Sat Jan 25 20:21:59 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:21:59 2014 : Debug:     response_window = 20
Sat Jan 25 20:21:59 2014 : Debug:     max_outstanding = 65536
Sat Jan 25 20:21:59 2014 : Debug:     require_message_authenticator = yes
Sat Jan 25 20:21:59 2014 : Debug:     zombie_period = 40
Sat Jan 25 20:21:59 2014 : Debug:     status_check = "status-server"
Sat Jan 25 20:21:59 2014 : Debug:     ping_interval = 30
Sat Jan 25 20:21:59 2014 : Debug:     check_interval = 30
Sat Jan 25 20:21:59 2014 : Debug:     num_answers_to_alive = 3
Sat Jan 25 20:21:59 2014 : Debug:     num_pings_to_alive = 3
Sat Jan 25 20:21:59 2014 : Debug:     revive_interval = 120
Sat Jan 25 20:21:59 2014 : Debug:     status_check_timeout = 4
Sat Jan 25 20:21:59 2014 : Debug:     irt = 2
Sat Jan 25 20:21:59 2014 : Debug:     mrt = 16
Sat Jan 25 20:21:59 2014 : Debug:     mrc = 5
Sat Jan 25 20:21:59 2014 : Debug:     mrd = 30
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  home_server_pool my_auth_failover {
Sat Jan 25 20:21:59 2014 : Debug:     type = fail-over
Sat Jan 25 20:21:59 2014 : Debug:     home_server = localhost
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  realm example.com {
Sat Jan 25 20:21:59 2014 : Debug:     auth_pool = my_auth_failover
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  realm LOCAL {
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Loading Clients ####
Sat Jan 25 20:21:59 2014 : Debug:  client localhost {
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:21:59 2014 : Debug:     require_message_authenticator = no
Sat Jan 25 20:21:59 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:21:59 2014 : Debug:     nastype = "other"
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Instantiating modules ####
Sat Jan 25 20:21:59 2014 : Debug:  instantiate {
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_exec
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sat Jan 25 20:21:59 2014 : Debug:   exec {
Sat Jan 25 20:21:59 2014 : Debug:     wait = no
Sat Jan 25 20:21:59 2014 : Debug:     input_pairs = "request"
Sat Jan 25 20:21:59 2014 : Debug:     shell_escape = yes
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:21:59 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sat Jan 25 20:21:59 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:21:59 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:21:59 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:21:59 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:21:59 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:21:59 2014 : Debug:     query = "SELECT  SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE  UserName='%{%k}'"
Sat Jan 25 20:21:59 2014 : Debug:     reset = "never"
Sat Jan 25 20:21:59 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:21:59 2014 : Debug:   sqlcounter noresetcounter {
Sat Jan 25 20:21:59 2014 : Debug:     counter-name = "Session-Timeout"
Sat Jan 25 20:21:59 2014 : Debug:     check-name = "Session-Timeout"
Sat Jan 25 20:21:59 2014 : Debug:     reply-name = "Session-Timeout"
Sat Jan 25 20:21:59 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:21:59 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:21:59 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 20:21:59 2014 : Debug:     reset = "never"
Sat Jan 25 20:21:59 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_expr
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_expiration
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sat Jan 25 20:21:59 2014 : Debug:   expiration {
Sat Jan 25 20:21:59 2014 : Debug:     reply-message = "Password Has Expired  "
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_logintime
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sat Jan 25 20:21:59 2014 : Debug:   logintime {
Sat Jan 25 20:21:59 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sat Jan 25 20:21:59 2014 : Debug:     minimum-timeout = 60
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sat Jan 25 20:21:59 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:21:59 2014 : Debug:  modules {
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_pap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sat Jan 25 20:21:59 2014 : Debug:   pap {
Sat Jan 25 20:21:59 2014 : Debug:     encryption_scheme = "auto"
Sat Jan 25 20:21:59 2014 : Debug:     auto_header = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_chap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_mschap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sat Jan 25 20:21:59 2014 : Debug:   mschap {
Sat Jan 25 20:21:59 2014 : Debug:     use_mppe = yes
Sat Jan 25 20:21:59 2014 : Debug:     require_encryption = no
Sat Jan 25 20:21:59 2014 : Debug:     require_strong = no
Sat Jan 25 20:21:59 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_unix
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sat Jan 25 20:21:59 2014 : Debug:   unix {
Sat Jan 25 20:21:59 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_eap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sat Jan 25 20:21:59 2014 : Debug:   eap {
Sat Jan 25 20:21:59 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:21:59 2014 : Debug:     timer_expire = 60
Sat Jan 25 20:21:59 2014 : Debug:     ignore_unknown_eap_types = no
Sat Jan 25 20:21:59 2014 : Debug:     cisco_accounting_username_bug = no
Sat Jan 25 20:21:59 2014 : Debug:     max_sessions = 4096
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-md5
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-leap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-gtc
Sat Jan 25 20:21:59 2014 : Debug:    gtc {
Sat Jan 25 20:21:59 2014 : Debug:     challenge = "Password: "
Sat Jan 25 20:21:59 2014 : Debug:     auth_type = "PAP"
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-tls
Sat Jan 25 20:21:59 2014 : Debug:    tls {
Sat Jan 25 20:21:59 2014 : Debug:     rsa_key_exchange = no
Sat Jan 25 20:21:59 2014 : Debug:     dh_key_exchange = yes
Sat Jan 25 20:21:59 2014 : Debug:     rsa_key_length = 512
Sat Jan 25 20:21:59 2014 : Debug:     dh_key_length = 512
Sat Jan 25 20:21:59 2014 : Debug:     verify_depth = 0
Sat Jan 25 20:21:59 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sat Jan 25 20:21:59 2014 : Debug:     pem_file_type = yes
Sat Jan 25 20:21:59 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sat Jan 25 20:21:59 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sat Jan 25 20:21:59 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sat Jan 25 20:21:59 2014 : Debug:     private_key_password = "whatever"
Sat Jan 25 20:21:59 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sat Jan 25 20:21:59 2014 : Debug:     random_file = "/dev/urandom"
Sat Jan 25 20:21:59 2014 : Debug:     fragment_size = 1024
Sat Jan 25 20:21:59 2014 : Debug:     include_length = yes
Sat Jan 25 20:21:59 2014 : Debug:     check_crl = no
Sat Jan 25 20:21:59 2014 : Debug:     cipher_list = "DEFAULT"
Sat Jan 25 20:21:59 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sat Jan 25 20:21:59 2014 : Debug:     cache {
Sat Jan 25 20:21:59 2014 : Debug:     enable = no
Sat Jan 25 20:21:59 2014 : Debug:     lifetime = 24
Sat Jan 25 20:21:59 2014 : Debug:     max_entries = 255
Sat Jan 25 20:21:59 2014 : Debug:     }
Sat Jan 25 20:21:59 2014 : Debug:     verify {
Sat Jan 25 20:21:59 2014 : Debug:     }
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-ttls
Sat Jan 25 20:21:59 2014 : Debug:    ttls {
Sat Jan 25 20:21:59 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:21:59 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:21:59 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:21:59 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:21:59 2014 : Debug:     include_length = yes
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-peap
Sat Jan 25 20:21:59 2014 : Debug:    peap {
Sat Jan 25 20:21:59 2014 : Debug:     default_eap_type = "mschapv2"
Sat Jan 25 20:21:59 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:21:59 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:21:59 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sat Jan 25 20:21:59 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-mschapv2
Sat Jan 25 20:21:59 2014 : Debug:    mschapv2 {
Sat Jan 25 20:21:59 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_realm
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sat Jan 25 20:21:59 2014 : Debug:   realm suffix {
Sat Jan 25 20:21:59 2014 : Debug:     format = "suffix"
Sat Jan 25 20:21:59 2014 : Debug:     delimiter = "@"
Sat Jan 25 20:21:59 2014 : Debug:     ignore_default = no
Sat Jan 25 20:21:59 2014 : Debug:     ignore_null = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_files
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sat Jan 25 20:21:59 2014 : Debug:   files {
Sat Jan 25 20:21:59 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sat Jan 25 20:21:59 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sat Jan 25 20:21:59 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sat Jan 25 20:21:59 2014 : Debug:     compat = "no"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_radutmp
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sat Jan 25 20:21:59 2014 : Debug:   radutmp {
Sat Jan 25 20:21:59 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sat Jan 25 20:21:59 2014 : Debug:     username = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:     case_sensitive = yes
Sat Jan 25 20:21:59 2014 : Debug:     check_with_nas = yes
Sat Jan 25 20:21:59 2014 : Debug:     perm = 384
Sat Jan 25 20:21:59 2014 : Debug:     callerid = yes
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "attr_filter.access_reject" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:21:59 2014 : Debug:   attr_filter attr_filter.access_reject {
Sat Jan 25 20:21:59 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sat Jan 25 20:21:59 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  } # modules
Sat Jan 25 20:21:59 2014 : Debug: } # server
Sat Jan 25 20:21:59 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sat Jan 25 20:21:59 2014 : Debug:  modules {
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_digest
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_preprocess
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sat Jan 25 20:21:59 2014 : Debug:   preprocess {
Sat Jan 25 20:21:59 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sat Jan 25 20:21:59 2014 : Debug:     hints = "/etc/freeradius/hints"
Sat Jan 25 20:21:59 2014 : Debug:     with_ascend_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     ascend_channels_per_line = 23
Sat Jan 25 20:21:59 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     with_specialix_jetstream_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     with_cisco_vsa_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     with_alvarion_vsa_hack = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_sql
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sat Jan 25 20:21:59 2014 : Debug:   sql {
Sat Jan 25 20:21:59 2014 : Debug:     driver = "rlm_sql_mysql"
Sat Jan 25 20:21:59 2014 : Debug:     server = "localhost"
Sat Jan 25 20:21:59 2014 : Debug:     port = ""
Sat Jan 25 20:21:59 2014 : Debug:     login = "radius"
Sat Jan 25 20:21:59 2014 : Debug:     password = "radpass"
Sat Jan 25 20:21:59 2014 : Debug:     radius_db = "radius"
Sat Jan 25 20:21:59 2014 : Debug:     read_groups = yes
Sat Jan 25 20:21:59 2014 : Debug:     sqltrace = no
Sat Jan 25 20:21:59 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sat Jan 25 20:21:59 2014 : Debug:     readclients = no
Sat Jan 25 20:21:59 2014 : Debug:     deletestalesessions = yes
Sat Jan 25 20:21:59 2014 : Debug:     num_sql_socks = 5
Sat Jan 25 20:21:59 2014 : Debug:     lifetime = 0
Sat Jan 25 20:21:59 2014 : Debug:     max_queries = 0
Sat Jan 25 20:21:59 2014 : Debug:     sql_user_name = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:     default_user_profile = ""
Sat Jan 25 20:21:59 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_check_query = "SELECT  id, username, attribute, value, op           FROM radcheck            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_reply_query = "SELECT  id, username, attribute, value, op           FROM radreply            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_group_check_query =  "SELECT id, groupname, attribute,           Value, op           FROM  radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_group_reply_query =  "SELECT id, groupname, attribute,           value, op           FROM  radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_onoff_query = "           UPDATE radacct           SET              acctstoptime       =  '%S',               acctsessiontime    =  unix_timestamp('%S') -                                     unix_timestamp(acctstarttime),               acctterminatecause =  '%{Acct-Terminate-Cause}',               acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE  acctstoptime IS NULL           AND nasipaddress      =   '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_update_query = "            UPDATE radacct           SET              framedipaddress =  '%{Framed-IP-Address}',              acctsessiontime     =  '%{Acct-Session-Time}',              acctinputoctets     =  '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                     '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets     = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                     '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username        =  '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_update_query_alt = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,       username,              realm,            nasipaddress,       nasportid,              nasporttype,      acctstarttime,      acctsessiontime,              acctauthentic,    connectinfo_start,  acctinputoctets,              acctoutputoctets, calledstationid,    callingstationid,              servicetype,      framedprotocol,     framedipaddress,              acctstartdelay,   xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                        INTERVAL (%{%{Acct-Session-Time}:-0} +                                  %{%{Acct-Delay-Time}:-0}) SECOND),                        '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',               '%{%{Acct-Input-Gigawords}:-0}' << 32 |               '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Service-Type}',  '%{Framed-Protocol}',              '%{Framed-IP-Address}',               '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_start_query = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,     nasportid,               nasporttype,      acctstarttime,    acctstoptime,               acctsessiontime,  acctauthentic,    connectinfo_start,               connectinfo_stop, acctinputoctets,  acctoutputoctets,               calledstationid,  callingstationid, acctterminatecause,               servicetype,      framedprotocol,   framedipaddress,               acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',               '%{SQL-User-Name}',              '%{Realm}',  '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',  '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',               '', '0', '0',              '%{Called-Station-Id}',  '%{Calling-Station-Id}', '',              '%{Service-Type}',  '%{Framed-Protocol}', '%{Framed-IP-Address}',               '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_start_query_alt = "            UPDATE radacct SET              acctstarttime     = '%S',               acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',               connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  =  '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'            AND nasipaddress     = '%{NAS-IP-Address}'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_stop_query = "            UPDATE radacct SET              acctstoptime       = '%S',               acctsessiontime    = '%{Acct-Session-Time}',               acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Input-Octets}:-0}',               acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}',               acctterminatecause = '%{Acct-Terminate-Cause}',               acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',               connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   =  '%{Acct-Session-Id}'           AND username          =  '%{SQL-User-Name}'           AND nasipaddress      =  '%{NAS-IP-Address}'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_stop_query_alt = "            INSERT INTO radacct             (acctsessionid, acctuniqueid,  username,              realm, nasipaddress, nasportid,               nasporttype, acctstarttime, acctstoptime,              acctsessiontime,  acctauthentic, connectinfo_start,              connectinfo_stop,  acctinputoctets, acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,  framedprotocol, framedipaddress,              acctstartdelay,  acctstopdelay)           VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                   INTERVAL (%{%{Acct-Session-Time}:-0} +                   %{%{Acct-Delay-Time}:-0}) SECOND),              '%S',  '%{Acct-Session-Time}', '%{Acct-Authentic}', '',               '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' <<  32 |              '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',               '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',               '0', '%{%{Acct-Delay-Time}:-0}')"
Sat Jan 25 20:21:59 2014 : Debug:     group_membership_query = "SELECT  groupname           FROM radusergroup           WHERE username =  '%{SQL-User-Name}'           ORDER BY priority"
Sat Jan 25 20:21:59 2014 : Debug:     connect_failure_retry_delay = 60
Sat Jan 25 20:21:59 2014 : Debug:     simul_count_query = ""
Sat Jan 25 20:21:59 2014 : Debug:     simul_verify_query = "SELECT  radacctid, acctsessionid, username,                                 nasipaddress, nasportid, framedipaddress,                                 callingstationid, framedprotocol                                FROM  radacct                                WHERE username =  '%{SQL-User-Name}'                                AND acctstoptime IS  NULL"
Sat Jan 25 20:21:59 2014 : Debug:     postauth_query = "INSERT INTO  radpostauth                           (username, pass, reply, authdate)                            VALUES (                            '%{User-Name}',                            '%{%{User-Password}:-%{Chap-Password}}',                            '%{reply:razz:acket-Type}', '%S')"
Sat Jan 25 20:21:59 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 20:21:59 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 20:21:59 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 20:21:59 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 20:21:59 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:21:59 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:21:59 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): Failed to connect to any SQL server.
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:21:59 2014 : Debug:   acct_unique {
Sat Jan 25 20:21:59 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_detail
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sat Jan 25 20:21:59 2014 : Debug:   detail {
Sat Jan 25 20:21:59 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sat Jan 25 20:21:59 2014 : Debug:     header = "%t"
Sat Jan 25 20:21:59 2014 : Debug:     detailperm = 384
Sat Jan 25 20:21:59 2014 : Debug:     dirperm = 493
Sat Jan 25 20:21:59 2014 : Debug:     locking = no
Sat Jan 25 20:21:59 2014 : Debug:     log_packet_header = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "attr_filter.accounting_response" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:21:59 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sat Jan 25 20:21:59 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sat Jan 25 20:21:59 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  } # modules
Sat Jan 25 20:21:59 2014 : Debug: } # server
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sat Jan 25 20:21:59 2014 : Debug: listen {
Sat Jan 25 20:21:59 2014 : Debug:     type = "auth"
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = *
Sat Jan 25 20:21:59 2014 : Debug:     port = 0
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: listen {
Sat Jan 25 20:21:59 2014 : Debug:     type = "acct"
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = *
Sat Jan 25 20:21:59 2014 : Debug:     port = 0
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: listen {
Sat Jan 25 20:21:59 2014 : Debug:     type = "auth"
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:21:59 2014 : Debug:     port = 18120
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: Listening on authentication address * port 1812
Sat Jan 25 20:21:59 2014 : Debug: Listening on accounting address * port 1813
Sat Jan 25 20:21:59 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sat Jan 25 20:21:59 2014 : Debug: Listening on proxy address * port 1814
Sat Jan 25 20:21:59 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 48863, id=148, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0x2a7f51cdc0487d4d306f642809d88b35
    CHAP-Password = 0x009c7ea5944ab7aaa1812e93ca907a492e
    Service-Type = Login-User
    Acct-Session-Id = "52e400ae00000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x28137849b1e1e0c80a83bed203f625f5
Sat Jan 25 20:22:30 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:30 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:22:30 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:22:30 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:22:30 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:22:30 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:22:30 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:22:30 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:22:30 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:22:30 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:22:30 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:22:30 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:22:30 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:22:30 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:22:30 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:22:30 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:22:30 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:22:30 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:30 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:22:30 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:22:30 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:22:30 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:22:30 2014 : Info: Delaying reject of request 0 for 1 seconds
Sat Jan 25 20:22:30 2014 : Debug: Going to the next request
Sat Jan 25 20:22:30 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:22:31 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 148 to 127.0.0.1 port 48863
Sat Jan 25 20:22:31 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:22:36 2014 : Info: Cleaning up request 0 ID 148 with timestamp +31
Sat Jan 25 20:22:36 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 53601, id=153, length=289
    ChilliSpot-Version = "1.2.9"
    User-Name = "lennon"
    CHAP-Challenge = 0x1f266e3bb2a51ebee4de6f7ce04ce257
    CHAP-Password = 0x00aa3b1325a1333f7a3099847ccbe938d2
    Service-Type = Login-User
    Acct-Session-Id = "52e400e700000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xa8771744d6c0a8fc0c58eee38f0b344b
Sat Jan 25 20:22:45 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:45 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:22:45 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:22:45 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:22:45 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:22:45 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:22:45 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:22:45 2014 : Info: [suffix] No '@' in User-Name = "lennon", looking up realm NULL
Sat Jan 25 20:22:45 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:22:45 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:22:45 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:22:45 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:22:45 2014 : Info: [sql]     expand: %{User-Name} -> lennon
Sat Jan 25 20:22:45 2014 : Info: [sql] sql_set_user escaped user --> 'lennon'
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:22:45 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:22:45 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:22:45 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:22:45 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:45 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:22:45 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> lennon
Sat Jan 25 20:22:45 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:22:45 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:22:45 2014 : Info: Delaying reject of request 1 for 1 seconds
Sat Jan 25 20:22:45 2014 : Debug: Going to the next request
Sat Jan 25 20:22:45 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:22:46 2014 : Info: Sending delayed reject for request 1
Sending Access-Reject of id 153 to 127.0.0.1 port 53601
Sat Jan 25 20:22:46 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:22:51 2014 : Info: Cleaning up request 1 ID 153 with timestamp +46
Sat Jan 25 20:22:51 2014 : Info: Ready to process requests.
 
```


my /etc/network/interfaces is as follows:

```
 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        gateway 192.168.2.1
        dns-nameservers 208.67.222.222 208.67.220.220


iface eth1 inet dhcp
        address 10.1.0.1
        netmask 255.255.255.0
        gateway 192.168.2.1
        dns-nameservers 10.1.0.1



```

compressed file of the directory /etc/freeradius
[ATTACH]249742[/ATTACH]


Apologies if i have not posted my question in a standard way, been looking for the instructions on how to post correctly, but cannot find them!

---

### Post by okay7675 on 2014-01-25
The output of ifconfig

root@ubuntu:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr d0:27:88:c0:e2:db  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:fec0:e2db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2807380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5274392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:200339806 (200.3 MB)  TX bytes:3473209941 (3.4 GB)
          Interrupt:41 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0a:cd:1f:f6:43  
          inet6 addr: fe80::20a:cdff:fe1f:f643/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:6801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:677278 (677.2 KB)  TX bytes:867521 (867.5 KB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:288412032 (288.4 MB)  TX bytes:288412032 (288.4 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.1.0.1  P-t-P:10.1.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING  MTU:1500  Metric:1
          RX packets:2723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:263708 (263.7 KB)  TX bytes:694695 (694.6 KB)

---

### Post by okay7675 on 2014-01-25
Hi 0651,

I've had the same problem as well, and I wonder if you have found a solution yet? What i have done is to create a new vendor and then create those attributes as follows:

Management > Attributes > New Vendor Attribute 

I then created an attribute for each of them (under the same vendor name), as follows:

[B]Vendor name - I put in any random name e.g. test
Attribute -name of the attribute e.g. Simultaneous-Use
Type - integer (honestly, i wasn't sure what to put here, but thats what some of the other default vendor attribute types were like)
Recommended table- either check or reply, depending on which attributes you are creating (so for example, for Session-Timeout, i created one attribute as a check, and another as a reply, since it appears under both check- and reply   attributes_
Recommended tool tip - left this blank
Recommended helper - left this blank, have no idea what it's about.


[/B]I did this for all the check and reply attributes under the single vendor name (in my case, test).

After adding the attributes to the vendor 'test', i then followed the instruction on


  **[FONT=&amp]Create Profiles – Time Based Profile[/FONT]**
  [FONT=&amp]Go to Management tab > Select Profiles > Create New Profiles >Add Profile Attributes[/FONT]
  [FONT=&amp]Type Profile Name, e.g. 60Mins

Select [B] Locate Attribute via Vendor/Attribute
[/B]Vendor- Select the vendor you created above, in my case, test
Attribute- Select the desired attribute, for example Session-Timeout
 and then click on 'add attribute'. a dialogue box will appear below
Under 'value' insert 3600 (for  Session-Timeout)
Op - i selected '=' for all of them, i'm not sure if this is correct though?
Target - check or reply (depending on whether its a check- or reply attribute)

Do this for all of the attributes by clicking add attribute and selecting the relevant information.
click 'apply' when you are done. 

I don't know if this will help you (i did this but my system is not yet running properly, so i have no idea if its the right thing. best wishes with  yours!)
[/FONT]

---

### Post by okay7675 on 2014-01-25
> **okay7675 said:**
> Hi laughmo,

I have the freeradius server up and running, but all my attempts at a client login are being rejected with the error* username and/or passowrd (sic) was not valid*.

I ran freeradius in debug mode and tried to connect, first as a member  user (username lennon) and then as a batch user (username omniWezkHeWq).  The results are in the attached file debug.txt

```

root@ubuntu:~# /etc/init.d/freeradius stop
 * Stopping FreeRADIUS daemon freeradius                                 [ OK ] 
root@ubuntu:~#  freeradius -XXX
Sat Jan 25 20:14:02 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sat Jan 25 20:14:02 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sat Jan 25 20:14:02 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sat Jan 25 20:14:02 2014 : Info: PARTICULAR PURPOSE. 
Sat Jan 25 20:14:02 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sat Jan 25 20:14:02 2014 : Info: GNU General Public License v2. 
Sat Jan 25 20:14:02 2014 : Info: Starting - reading configuration files ...
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sat Jan 25 20:14:02 2014 : Debug: including files in directory /etc/freeradius/modules/
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sat Jan 25 20:14:02 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:14:02 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:14:02 2014 : Debug: main {
Sat Jan 25 20:14:02 2014 : Debug:     user = "freerad"
Sat Jan 25 20:14:02 2014 : Debug:     group = "freerad"
Sat Jan 25 20:14:02 2014 : Debug:     allow_core_dumps = no
Sat Jan 25 20:14:02 2014 : Debug: }
Sat Jan 25 20:14:02 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sat Jan 25 20:14:03 2014 : Debug: main {
Sat Jan 25 20:14:03 2014 : Debug:     prefix = "/usr"
Sat Jan 25 20:14:03 2014 : Debug:     localstatedir = "/var"
Sat Jan 25 20:14:03 2014 : Debug:     logdir = "/var/log/freeradius"
Sat Jan 25 20:14:03 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sat Jan 25 20:14:03 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sat Jan 25 20:14:03 2014 : Debug:     hostname_lookups = no
Sat Jan 25 20:14:03 2014 : Debug:     max_request_time = 30
Sat Jan 25 20:14:03 2014 : Debug:     cleanup_delay = 5
Sat Jan 25 20:14:03 2014 : Debug:     max_requests = 1024
Sat Jan 25 20:14:03 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sat Jan 25 20:14:03 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sat Jan 25 20:14:03 2014 : Debug:     debug_level = 0
Sat Jan 25 20:14:03 2014 : Debug:     proxy_requests = yes
Sat Jan 25 20:14:03 2014 : Debug:  log {
Sat Jan 25 20:14:03 2014 : Debug:     stripped_names = no
Sat Jan 25 20:14:03 2014 : Debug:     auth = no
Sat Jan 25 20:14:03 2014 : Debug:     auth_badpass = no
Sat Jan 25 20:14:03 2014 : Debug:     auth_goodpass = no
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  security {
Sat Jan 25 20:14:03 2014 : Debug:     max_attributes = 200
Sat Jan 25 20:14:03 2014 : Debug:     reject_delay = 1
Sat Jan 25 20:14:03 2014 : Debug:     status_server = yes
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sat Jan 25 20:14:03 2014 : Debug:  proxy server {
Sat Jan 25 20:14:03 2014 : Debug:     retry_delay = 5
Sat Jan 25 20:14:03 2014 : Debug:     retry_count = 3
Sat Jan 25 20:14:03 2014 : Debug:     default_fallback = no
Sat Jan 25 20:14:03 2014 : Debug:     dead_time = 120
Sat Jan 25 20:14:03 2014 : Debug:     wake_all_if_all_dead = no
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  home_server localhost {
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:14:03 2014 : Debug:     port = 1812
Sat Jan 25 20:14:03 2014 : Debug:     type = "auth"
Sat Jan 25 20:14:03 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:14:03 2014 : Debug:     response_window = 20
Sat Jan 25 20:14:03 2014 : Debug:     max_outstanding = 65536
Sat Jan 25 20:14:03 2014 : Debug:     require_message_authenticator = yes
Sat Jan 25 20:14:03 2014 : Debug:     zombie_period = 40
Sat Jan 25 20:14:03 2014 : Debug:     status_check = "status-server"
Sat Jan 25 20:14:03 2014 : Debug:     ping_interval = 30
Sat Jan 25 20:14:03 2014 : Debug:     check_interval = 30
Sat Jan 25 20:14:03 2014 : Debug:     num_answers_to_alive = 3
Sat Jan 25 20:14:03 2014 : Debug:     num_pings_to_alive = 3
Sat Jan 25 20:14:03 2014 : Debug:     revive_interval = 120
Sat Jan 25 20:14:03 2014 : Debug:     status_check_timeout = 4
Sat Jan 25 20:14:03 2014 : Debug:     irt = 2
Sat Jan 25 20:14:03 2014 : Debug:     mrt = 16
Sat Jan 25 20:14:03 2014 : Debug:     mrc = 5
Sat Jan 25 20:14:03 2014 : Debug:     mrd = 30
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  home_server_pool my_auth_failover {
Sat Jan 25 20:14:03 2014 : Debug:     type = fail-over
Sat Jan 25 20:14:03 2014 : Debug:     home_server = localhost
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  realm example.com {
Sat Jan 25 20:14:03 2014 : Debug:     auth_pool = my_auth_failover
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug:  realm LOCAL {
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Loading Clients ####
Sat Jan 25 20:14:03 2014 : Debug:  client localhost {
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:14:03 2014 : Debug:     require_message_authenticator = no
Sat Jan 25 20:14:03 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:14:03 2014 : Debug:     nastype = "other"
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Instantiating modules ####
Sat Jan 25 20:14:03 2014 : Debug:  instantiate {
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_exec
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sat Jan 25 20:14:03 2014 : Debug:   exec {
Sat Jan 25 20:14:03 2014 : Debug:     wait = no
Sat Jan 25 20:14:03 2014 : Debug:     input_pairs = "request"
Sat Jan 25 20:14:03 2014 : Debug:     shell_escape = yes
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:14:03 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sat Jan 25 20:14:03 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:14:03 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:14:03 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:14:03 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:14:03 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:14:03 2014 : Debug:     query = "SELECT  SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE  UserName='%{%k}'"
Sat Jan 25 20:14:03 2014 : Debug:     reset = "never"
Sat Jan 25 20:14:03 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:14:03 2014 : Debug:   sqlcounter noresetcounter {
Sat Jan 25 20:14:03 2014 : Debug:     counter-name = "Session-Timeout"
Sat Jan 25 20:14:03 2014 : Debug:     check-name = "Session-Timeout"
Sat Jan 25 20:14:03 2014 : Debug:     reply-name = "Session-Timeout"
Sat Jan 25 20:14:03 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:14:03 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:14:03 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 20:14:03 2014 : Debug:     reset = "never"
Sat Jan 25 20:14:03 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug: rlm_sqlcounter: Current Time:  1390673643 [2014-01-25 20:14:03], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_expr
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_expiration
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sat Jan 25 20:14:03 2014 : Debug:   expiration {
Sat Jan 25 20:14:03 2014 : Debug:     reply-message = "Password Has Expired  "
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_logintime
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sat Jan 25 20:14:03 2014 : Debug:   logintime {
Sat Jan 25 20:14:03 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sat Jan 25 20:14:03 2014 : Debug:     minimum-timeout = 60
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  }
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sat Jan 25 20:14:03 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:14:03 2014 : Debug:  modules {
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_pap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sat Jan 25 20:14:03 2014 : Debug:   pap {
Sat Jan 25 20:14:03 2014 : Debug:     encryption_scheme = "auto"
Sat Jan 25 20:14:03 2014 : Debug:     auto_header = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_chap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_mschap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sat Jan 25 20:14:03 2014 : Debug:   mschap {
Sat Jan 25 20:14:03 2014 : Debug:     use_mppe = yes
Sat Jan 25 20:14:03 2014 : Debug:     require_encryption = no
Sat Jan 25 20:14:03 2014 : Debug:     require_strong = no
Sat Jan 25 20:14:03 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_unix
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sat Jan 25 20:14:03 2014 : Debug:   unix {
Sat Jan 25 20:14:03 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_eap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sat Jan 25 20:14:03 2014 : Debug:   eap {
Sat Jan 25 20:14:03 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:14:03 2014 : Debug:     timer_expire = 60
Sat Jan 25 20:14:03 2014 : Debug:     ignore_unknown_eap_types = no
Sat Jan 25 20:14:03 2014 : Debug:     cisco_accounting_username_bug = no
Sat Jan 25 20:14:03 2014 : Debug:     max_sessions = 4096
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-md5
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-leap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-gtc
Sat Jan 25 20:14:03 2014 : Debug:    gtc {
Sat Jan 25 20:14:03 2014 : Debug:     challenge = "Password: "
Sat Jan 25 20:14:03 2014 : Debug:     auth_type = "PAP"
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-tls
Sat Jan 25 20:14:03 2014 : Debug:    tls {
Sat Jan 25 20:14:03 2014 : Debug:     rsa_key_exchange = no
Sat Jan 25 20:14:03 2014 : Debug:     dh_key_exchange = yes
Sat Jan 25 20:14:03 2014 : Debug:     rsa_key_length = 512
Sat Jan 25 20:14:03 2014 : Debug:     dh_key_length = 512
Sat Jan 25 20:14:03 2014 : Debug:     verify_depth = 0
Sat Jan 25 20:14:03 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sat Jan 25 20:14:03 2014 : Debug:     pem_file_type = yes
Sat Jan 25 20:14:03 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sat Jan 25 20:14:03 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sat Jan 25 20:14:03 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sat Jan 25 20:14:03 2014 : Debug:     private_key_password = "whatever"
Sat Jan 25 20:14:03 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sat Jan 25 20:14:03 2014 : Debug:     random_file = "/dev/urandom"
Sat Jan 25 20:14:03 2014 : Debug:     fragment_size = 1024
Sat Jan 25 20:14:03 2014 : Debug:     include_length = yes
Sat Jan 25 20:14:03 2014 : Debug:     check_crl = no
Sat Jan 25 20:14:03 2014 : Debug:     cipher_list = "DEFAULT"
Sat Jan 25 20:14:03 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sat Jan 25 20:14:03 2014 : Debug:     cache {
Sat Jan 25 20:14:03 2014 : Debug:     enable = no
Sat Jan 25 20:14:03 2014 : Debug:     lifetime = 24
Sat Jan 25 20:14:03 2014 : Debug:     max_entries = 255
Sat Jan 25 20:14:03 2014 : Debug:     }
Sat Jan 25 20:14:03 2014 : Debug:     verify {
Sat Jan 25 20:14:03 2014 : Debug:     }
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-ttls
Sat Jan 25 20:14:03 2014 : Debug:    ttls {
Sat Jan 25 20:14:03 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:14:03 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:14:03 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:14:03 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:14:03 2014 : Debug:     include_length = yes
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-peap
Sat Jan 25 20:14:03 2014 : Debug:    peap {
Sat Jan 25 20:14:03 2014 : Debug:     default_eap_type = "mschapv2"
Sat Jan 25 20:14:03 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:14:03 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:14:03 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sat Jan 25 20:14:03 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating eap-mschapv2
Sat Jan 25 20:14:03 2014 : Debug:    mschapv2 {
Sat Jan 25 20:14:03 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:14:03 2014 : Debug:    }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_realm
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sat Jan 25 20:14:03 2014 : Debug:   realm suffix {
Sat Jan 25 20:14:03 2014 : Debug:     format = "suffix"
Sat Jan 25 20:14:03 2014 : Debug:     delimiter = "@"
Sat Jan 25 20:14:03 2014 : Debug:     ignore_default = no
Sat Jan 25 20:14:03 2014 : Debug:     ignore_null = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_files
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sat Jan 25 20:14:03 2014 : Debug:   files {
Sat Jan 25 20:14:03 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sat Jan 25 20:14:03 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sat Jan 25 20:14:03 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sat Jan 25 20:14:03 2014 : Debug:     compat = "no"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_radutmp
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sat Jan 25 20:14:03 2014 : Debug:   radutmp {
Sat Jan 25 20:14:03 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sat Jan 25 20:14:03 2014 : Debug:     username = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:     case_sensitive = yes
Sat Jan 25 20:14:03 2014 : Debug:     check_with_nas = yes
Sat Jan 25 20:14:03 2014 : Debug:     perm = 384
Sat Jan 25 20:14:03 2014 : Debug:     callerid = yes
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "attr_filter.access_reject" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:14:03 2014 : Debug:   attr_filter attr_filter.access_reject {
Sat Jan 25 20:14:03 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sat Jan 25 20:14:03 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  } # modules
Sat Jan 25 20:14:03 2014 : Debug: } # server
Sat Jan 25 20:14:03 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sat Jan 25 20:14:03 2014 : Debug:  modules {
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_digest
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_preprocess
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sat Jan 25 20:14:03 2014 : Debug:   preprocess {
Sat Jan 25 20:14:03 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sat Jan 25 20:14:03 2014 : Debug:     hints = "/etc/freeradius/hints"
Sat Jan 25 20:14:03 2014 : Debug:     with_ascend_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     ascend_channels_per_line = 23
Sat Jan 25 20:14:03 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     with_specialix_jetstream_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     with_cisco_vsa_hack = no
Sat Jan 25 20:14:03 2014 : Debug:     with_alvarion_vsa_hack = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_sql
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sat Jan 25 20:14:03 2014 : Debug:   sql {
Sat Jan 25 20:14:03 2014 : Debug:     driver = "rlm_sql_mysql"
Sat Jan 25 20:14:03 2014 : Debug:     server = "localhost"
Sat Jan 25 20:14:03 2014 : Debug:     port = ""
Sat Jan 25 20:14:03 2014 : Debug:     login = "radius"
Sat Jan 25 20:14:03 2014 : Debug:     password = "radpass"
Sat Jan 25 20:14:03 2014 : Debug:     radius_db = "radius"
Sat Jan 25 20:14:03 2014 : Debug:     read_groups = yes
Sat Jan 25 20:14:03 2014 : Debug:     sqltrace = no
Sat Jan 25 20:14:03 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sat Jan 25 20:14:03 2014 : Debug:     readclients = no
Sat Jan 25 20:14:03 2014 : Debug:     deletestalesessions = yes
Sat Jan 25 20:14:03 2014 : Debug:     num_sql_socks = 5
Sat Jan 25 20:14:03 2014 : Debug:     lifetime = 0
Sat Jan 25 20:14:03 2014 : Debug:     max_queries = 0
Sat Jan 25 20:14:03 2014 : Debug:     sql_user_name = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:     default_user_profile = ""
Sat Jan 25 20:14:03 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_check_query = "SELECT  id, username, attribute, value, op           FROM radcheck            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_reply_query = "SELECT  id, username, attribute, value, op           FROM radreply            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_group_check_query =  "SELECT id, groupname, attribute,           Value, op           FROM  radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:14:03 2014 : Debug:     authorize_group_reply_query =  "SELECT id, groupname, attribute,           value, op           FROM  radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_onoff_query = "           UPDATE radacct           SET              acctstoptime       =  '%S',               acctsessiontime    =  unix_timestamp('%S') -                                     unix_timestamp(acctstarttime),               acctterminatecause =  '%{Acct-Terminate-Cause}',               acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE  acctstoptime IS NULL           AND nasipaddress      =   '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_update_query = "            UPDATE radacct           SET              framedipaddress =  '%{Framed-IP-Address}',              acctsessiontime     =  '%{Acct-Session-Time}',              acctinputoctets     =  '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                     '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets     = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                     '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username        =  '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_update_query_alt = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,       username,              realm,            nasipaddress,       nasportid,              nasporttype,      acctstarttime,      acctsessiontime,              acctauthentic,    connectinfo_start,  acctinputoctets,              acctoutputoctets, calledstationid,    callingstationid,              servicetype,      framedprotocol,     framedipaddress,              acctstartdelay,   xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                        INTERVAL (%{%{Acct-Session-Time}:-0} +                                  %{%{Acct-Delay-Time}:-0}) SECOND),                        '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',               '%{%{Acct-Input-Gigawords}:-0}' << 32 |               '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Service-Type}',  '%{Framed-Protocol}',              '%{Framed-IP-Address}',               '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_start_query = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,     nasportid,               nasporttype,      acctstarttime,    acctstoptime,               acctsessiontime,  acctauthentic,    connectinfo_start,               connectinfo_stop, acctinputoctets,  acctoutputoctets,               calledstationid,  callingstationid, acctterminatecause,               servicetype,      framedprotocol,   framedipaddress,               acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',               '%{SQL-User-Name}',              '%{Realm}',  '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',  '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',               '', '0', '0',              '%{Called-Station-Id}',  '%{Calling-Station-Id}', '',              '%{Service-Type}',  '%{Framed-Protocol}', '%{Framed-IP-Address}',               '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_start_query_alt = "            UPDATE radacct SET              acctstarttime     = '%S',               acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',               connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  =  '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'            AND nasipaddress     = '%{NAS-IP-Address}'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_stop_query = "            UPDATE radacct SET              acctstoptime       = '%S',               acctsessiontime    = '%{Acct-Session-Time}',               acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Input-Octets}:-0}',               acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}',               acctterminatecause = '%{Acct-Terminate-Cause}',               acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',               connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   =  '%{Acct-Session-Id}'           AND username          =  '%{SQL-User-Name}'           AND nasipaddress      =  '%{NAS-IP-Address}'"
Sat Jan 25 20:14:03 2014 : Debug:     accounting_stop_query_alt = "            INSERT INTO radacct             (acctsessionid, acctuniqueid,  username,              realm, nasipaddress, nasportid,               nasporttype, acctstarttime, acctstoptime,              acctsessiontime,  acctauthentic, connectinfo_start,              connectinfo_stop,  acctinputoctets, acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,  framedprotocol, framedipaddress,              acctstartdelay,  acctstopdelay)           VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                   INTERVAL (%{%{Acct-Session-Time}:-0} +                   %{%{Acct-Delay-Time}:-0}) SECOND),              '%S',  '%{Acct-Session-Time}', '%{Acct-Authentic}', '',               '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' <<  32 |              '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',               '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',               '0', '%{%{Acct-Delay-Time}:-0}')"
Sat Jan 25 20:14:03 2014 : Debug:     group_membership_query = "SELECT  groupname           FROM radusergroup           WHERE username =  '%{SQL-User-Name}'           ORDER BY priority"
Sat Jan 25 20:14:03 2014 : Debug:     connect_failure_retry_delay = 60
Sat Jan 25 20:14:03 2014 : Debug:     simul_count_query = ""
Sat Jan 25 20:14:03 2014 : Debug:     simul_verify_query = "SELECT  radacctid, acctsessionid, username,                                 nasipaddress, nasportid, framedipaddress,                                 callingstationid, framedprotocol                                FROM  radacct                                WHERE username =  '%{SQL-User-Name}'                                AND acctstoptime IS  NULL"
Sat Jan 25 20:14:03 2014 : Debug:     postauth_query = "INSERT INTO  radpostauth                           (username, pass, reply, authdate)                            VALUES (                            '%{User-Name}',                            '%{%{User-Password}:-%{Chap-Password}}',                            '%{reply:razz:acket-Type}', '%S')"
Sat Jan 25 20:14:03 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 20:14:03 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 20:14:03 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 20:14:03 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 20:14:03 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:14:03 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:14:03 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 20:14:03 2014 : Debug: rlm_sql (sql): Failed to connect to any SQL server.
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:14:03 2014 : Debug:   acct_unique {
Sat Jan 25 20:14:03 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sat Jan 25 20:14:03 2014 : Debug:  Module: Linked to module rlm_detail
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sat Jan 25 20:14:03 2014 : Debug:   detail {
Sat Jan 25 20:14:03 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sat Jan 25 20:14:03 2014 : Debug:     header = "%t"
Sat Jan 25 20:14:03 2014 : Debug:     detailperm = 384
Sat Jan 25 20:14:03 2014 : Debug:     dirperm = 493
Sat Jan 25 20:14:03 2014 : Debug:     locking = no
Sat Jan 25 20:14:03 2014 : Debug:     log_packet_header = no
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Instantiating module  "attr_filter.accounting_response" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:14:03 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sat Jan 25 20:14:03 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sat Jan 25 20:14:03 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:14:03 2014 : Debug:   }
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:14:03 2014 : Debug:  } # modules
Sat Jan 25 20:14:03 2014 : Debug: } # server
Sat Jan 25 20:14:03 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sat Jan 25 20:14:03 2014 : Debug: listen {
Sat Jan 25 20:14:03 2014 : Debug:     type = "auth"
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = *
Sat Jan 25 20:14:03 2014 : Debug:     port = 0
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: listen {
Sat Jan 25 20:14:03 2014 : Debug:     type = "acct"
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = *
Sat Jan 25 20:14:03 2014 : Debug:     port = 0
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: listen {
Sat Jan 25 20:14:03 2014 : Debug:     type = "auth"
Sat Jan 25 20:14:03 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:14:03 2014 : Debug:     port = 18120
Sat Jan 25 20:14:03 2014 : Debug: }
Sat Jan 25 20:14:03 2014 : Debug: Listening on authentication address * port 1812
Sat Jan 25 20:14:03 2014 : Debug: Listening on accounting address * port 1813
Sat Jan 25 20:14:03 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sat Jan 25 20:14:03 2014 : Debug: Listening on proxy address * port 1814
Sat Jan 25 20:14:03 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 40294, id=116, length=289
    ChilliSpot-Version = "1.2.9"
    User-Name = "lennon"
    CHAP-Challenge = 0xd837ab6ba881992c454c811ef30d8d1f
    CHAP-Password = 0x00bfacbbd38f831e6c26aef87a71350efd
    Service-Type = Login-User
    Acct-Session-Id = "52e3f80800000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x1a7d60176ce601b1aa9216e2c15b662b
Sat Jan 25 20:14:09 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:14:09 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:14:09 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:14:09 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:14:09 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:14:09 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:14:09 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:14:09 2014 : Info: [suffix] No '@' in User-Name = "lennon", looking up realm NULL
Sat Jan 25 20:14:09 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:14:09 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:14:09 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:14:09 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:14:09 2014 : Info: [sql]     expand: %{User-Name} -> lennon
Sat Jan 25 20:14:09 2014 : Info: [sql] sql_set_user escaped user --> 'lennon'
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:14:09 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:14:09 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:14:09 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:14:09 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:14:09 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:14:09 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:14:09 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> lennon
Sat Jan 25 20:14:09 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:14:09 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:14:09 2014 : Info: Delaying reject of request 0 for 1 seconds
Sat Jan 25 20:14:09 2014 : Debug: Going to the next request
Sat Jan 25 20:14:09 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:14:10 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 116 to 127.0.0.1 port 40294
Sat Jan 25 20:14:10 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:14:15 2014 : Info: Cleaning up request 0 ID 116 with timestamp +6
Sat Jan 25 20:14:15 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 41071, id=131, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0xb1d31df75780c9a095f3fe4d253860e4
    CHAP-Password = 0x00fc4cb7a9a433cccb18d0a3bcd8157449
    Service-Type = Login-User
    Acct-Session-Id = "52e3fef200000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x40328b5cd3fada0c2342ef5a7162736a
Sat Jan 25 20:20:24 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:20:24 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:20:24 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:20:24 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:20:24 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:20:24 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:20:24 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:20:24 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:20:24 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:20:24 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:20:24 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:20:24 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:20:24 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:20:24 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:20:24 2014 : Info: rlm_sql (sql): Trying to (re)connect unconnected handle 4..
Sat Jan 25 20:20:24 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 20:20:24 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 20:20:24 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:20:24 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:20:24 2014 : Error: rlm_sql (sql): Failed to connect DB handle #4
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:20:24 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:20:24 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 1
Sat Jan 25 20:20:24 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:20:24 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:20:24 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:20:24 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:20:24 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:20:24 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:20:24 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:20:24 2014 : Info: Delaying reject of request 1 for 1 seconds
Sat Jan 25 20:20:24 2014 : Debug: Going to the next request
Sat Jan 25 20:20:24 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:20:25 2014 : Info: Sending delayed reject for request 1
Sending Access-Reject of id 131 to 127.0.0.1 port 41071
Sat Jan 25 20:20:25 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:20:30 2014 : Info: Cleaning up request 1 ID 131 with timestamp +381
Sat Jan 25 20:20:30 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 60503, id=138, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0xff74f6e4b14087b180e55e8306e3e632
    CHAP-Password = 0x00f653d2c9d713a0854114d69d1ea166f8
    Service-Type = Login-User
    Acct-Session-Id = "52e4006900000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xbe5f9af59a3ffda37ad836e3b44dacd9
Sat Jan 25 20:21:29 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:29 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:21:29 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:21:29 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:21:29 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:21:29 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:21:29 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:21:29 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:21:29 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:21:29 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:21:29 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:21:29 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:21:29 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:29 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:21:29 2014 : Info: rlm_sql (sql): Trying to (re)connect unconnected handle 4..
Sat Jan 25 20:21:29 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 20:21:29 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 20:21:29 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:21:29 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:21:29 2014 : Error: rlm_sql (sql): Failed to connect DB handle #4
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:21:29 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:21:29 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 1
Sat Jan 25 20:21:29 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:21:29 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:21:29 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:29 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:21:29 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:29 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:21:29 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:21:29 2014 : Info: Delaying reject of request 2 for 1 seconds
Sat Jan 25 20:21:29 2014 : Debug: Going to the next request
Sat Jan 25 20:21:29 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:21:30 2014 : Info: Sending delayed reject for request 2
Sending Access-Reject of id 138 to 127.0.0.1 port 60503
Sat Jan 25 20:21:30 2014 : Debug: Waking up in 4.9 seconds.
rad_recv: Access-Request packet from host 127.0.0.1 port 37727, id=142, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0x3623bc4ba66d7d5b48d185158fb0b8fb
    CHAP-Password = 0x0005221589b8b7f85d79a2b774f62f6657
    Service-Type = Login-User
    Acct-Session-Id = "52e400aa00000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xb2649e5fca7e2612485ada443a70d46c
Sat Jan 25 20:21:33 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:33 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:21:33 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:21:33 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:21:33 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:21:33 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:21:33 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:21:33 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:21:33 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:21:33 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:21:33 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:21:33 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:21:33 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:33 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:21:33 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:21:33 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:21:33 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:21:33 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:21:33 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:33 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:21:33 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:21:33 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:21:33 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:21:33 2014 : Info: Delaying reject of request 3 for 1 seconds
Sat Jan 25 20:21:33 2014 : Debug: Going to the next request
Sat Jan 25 20:21:33 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:21:34 2014 : Info: Sending delayed reject for request 3
Sending Access-Reject of id 142 to 127.0.0.1 port 37727
Sat Jan 25 20:21:34 2014 : Debug: Waking up in 1.0 seconds.
Sat Jan 25 20:21:35 2014 : Info: Cleaning up request 2 ID 138 with timestamp +446
Sat Jan 25 20:21:35 2014 : Debug: Waking up in 3.9 seconds.
Sat Jan 25 20:21:39 2014 : Info: Cleaning up request 3 ID 142 with timestamp +450
Sat Jan 25 20:21:39 2014 : Info: Ready to process requests.
^C
root@ubuntu:~# clear

root@ubuntu:~# freeradisu -XXX
No command 'freeradisu' found, did you mean:
 Command 'freeradius' from package 'freeradius' (main)
freeradisu: command not found
root@ubuntu:~# freeradius -XXX
Sat Jan 25 20:21:59 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sat Jan 25 20:21:59 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sat Jan 25 20:21:59 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sat Jan 25 20:21:59 2014 : Info: PARTICULAR PURPOSE. 
Sat Jan 25 20:21:59 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sat Jan 25 20:21:59 2014 : Info: GNU General Public License v2. 
Sat Jan 25 20:21:59 2014 : Info: Starting - reading configuration files ...
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sat Jan 25 20:21:59 2014 : Debug: including files in directory /etc/freeradius/modules/
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sat Jan 25 20:21:59 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:21:59 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:21:59 2014 : Debug: main {
Sat Jan 25 20:21:59 2014 : Debug:     user = "freerad"
Sat Jan 25 20:21:59 2014 : Debug:     group = "freerad"
Sat Jan 25 20:21:59 2014 : Debug:     allow_core_dumps = no
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sat Jan 25 20:21:59 2014 : Debug: main {
Sat Jan 25 20:21:59 2014 : Debug:     prefix = "/usr"
Sat Jan 25 20:21:59 2014 : Debug:     localstatedir = "/var"
Sat Jan 25 20:21:59 2014 : Debug:     logdir = "/var/log/freeradius"
Sat Jan 25 20:21:59 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sat Jan 25 20:21:59 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sat Jan 25 20:21:59 2014 : Debug:     hostname_lookups = no
Sat Jan 25 20:21:59 2014 : Debug:     max_request_time = 30
Sat Jan 25 20:21:59 2014 : Debug:     cleanup_delay = 5
Sat Jan 25 20:21:59 2014 : Debug:     max_requests = 1024
Sat Jan 25 20:21:59 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sat Jan 25 20:21:59 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sat Jan 25 20:21:59 2014 : Debug:     debug_level = 0
Sat Jan 25 20:21:59 2014 : Debug:     proxy_requests = yes
Sat Jan 25 20:21:59 2014 : Debug:  log {
Sat Jan 25 20:21:59 2014 : Debug:     stripped_names = no
Sat Jan 25 20:21:59 2014 : Debug:     auth = no
Sat Jan 25 20:21:59 2014 : Debug:     auth_badpass = no
Sat Jan 25 20:21:59 2014 : Debug:     auth_goodpass = no
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  security {
Sat Jan 25 20:21:59 2014 : Debug:     max_attributes = 200
Sat Jan 25 20:21:59 2014 : Debug:     reject_delay = 1
Sat Jan 25 20:21:59 2014 : Debug:     status_server = yes
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sat Jan 25 20:21:59 2014 : Debug:  proxy server {
Sat Jan 25 20:21:59 2014 : Debug:     retry_delay = 5
Sat Jan 25 20:21:59 2014 : Debug:     retry_count = 3
Sat Jan 25 20:21:59 2014 : Debug:     default_fallback = no
Sat Jan 25 20:21:59 2014 : Debug:     dead_time = 120
Sat Jan 25 20:21:59 2014 : Debug:     wake_all_if_all_dead = no
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  home_server localhost {
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:21:59 2014 : Debug:     port = 1812
Sat Jan 25 20:21:59 2014 : Debug:     type = "auth"
Sat Jan 25 20:21:59 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:21:59 2014 : Debug:     response_window = 20
Sat Jan 25 20:21:59 2014 : Debug:     max_outstanding = 65536
Sat Jan 25 20:21:59 2014 : Debug:     require_message_authenticator = yes
Sat Jan 25 20:21:59 2014 : Debug:     zombie_period = 40
Sat Jan 25 20:21:59 2014 : Debug:     status_check = "status-server"
Sat Jan 25 20:21:59 2014 : Debug:     ping_interval = 30
Sat Jan 25 20:21:59 2014 : Debug:     check_interval = 30
Sat Jan 25 20:21:59 2014 : Debug:     num_answers_to_alive = 3
Sat Jan 25 20:21:59 2014 : Debug:     num_pings_to_alive = 3
Sat Jan 25 20:21:59 2014 : Debug:     revive_interval = 120
Sat Jan 25 20:21:59 2014 : Debug:     status_check_timeout = 4
Sat Jan 25 20:21:59 2014 : Debug:     irt = 2
Sat Jan 25 20:21:59 2014 : Debug:     mrt = 16
Sat Jan 25 20:21:59 2014 : Debug:     mrc = 5
Sat Jan 25 20:21:59 2014 : Debug:     mrd = 30
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  home_server_pool my_auth_failover {
Sat Jan 25 20:21:59 2014 : Debug:     type = fail-over
Sat Jan 25 20:21:59 2014 : Debug:     home_server = localhost
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  realm example.com {
Sat Jan 25 20:21:59 2014 : Debug:     auth_pool = my_auth_failover
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug:  realm LOCAL {
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Loading Clients ####
Sat Jan 25 20:21:59 2014 : Debug:  client localhost {
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:21:59 2014 : Debug:     require_message_authenticator = no
Sat Jan 25 20:21:59 2014 : Debug:     secret = "testing123"
Sat Jan 25 20:21:59 2014 : Debug:     nastype = "other"
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Instantiating modules ####
Sat Jan 25 20:21:59 2014 : Debug:  instantiate {
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_exec
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sat Jan 25 20:21:59 2014 : Debug:   exec {
Sat Jan 25 20:21:59 2014 : Debug:     wait = no
Sat Jan 25 20:21:59 2014 : Debug:     input_pairs = "request"
Sat Jan 25 20:21:59 2014 : Debug:     shell_escape = yes
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:21:59 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sat Jan 25 20:21:59 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:21:59 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:21:59 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 20:21:59 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:21:59 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:21:59 2014 : Debug:     query = "SELECT  SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE  UserName='%{%k}'"
Sat Jan 25 20:21:59 2014 : Debug:     reset = "never"
Sat Jan 25 20:21:59 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 20:21:59 2014 : Debug:   sqlcounter noresetcounter {
Sat Jan 25 20:21:59 2014 : Debug:     counter-name = "Session-Timeout"
Sat Jan 25 20:21:59 2014 : Debug:     check-name = "Session-Timeout"
Sat Jan 25 20:21:59 2014 : Debug:     reply-name = "Session-Timeout"
Sat Jan 25 20:21:59 2014 : Debug:     key = "User-Name"
Sat Jan 25 20:21:59 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 20:21:59 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 20:21:59 2014 : Debug:     reset = "never"
Sat Jan 25 20:21:59 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Next reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug: rlm_sqlcounter: Current Time:  1390674119 [2014-01-25 20:21:59], Prev reset 0 [2014-01-25 20:00:00]
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_expr
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_expiration
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sat Jan 25 20:21:59 2014 : Debug:   expiration {
Sat Jan 25 20:21:59 2014 : Debug:     reply-message = "Password Has Expired  "
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_logintime
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sat Jan 25 20:21:59 2014 : Debug:   logintime {
Sat Jan 25 20:21:59 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sat Jan 25 20:21:59 2014 : Debug:     minimum-timeout = 60
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  }
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sat Jan 25 20:21:59 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 20:21:59 2014 : Debug:  modules {
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_pap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sat Jan 25 20:21:59 2014 : Debug:   pap {
Sat Jan 25 20:21:59 2014 : Debug:     encryption_scheme = "auto"
Sat Jan 25 20:21:59 2014 : Debug:     auto_header = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_chap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_mschap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sat Jan 25 20:21:59 2014 : Debug:   mschap {
Sat Jan 25 20:21:59 2014 : Debug:     use_mppe = yes
Sat Jan 25 20:21:59 2014 : Debug:     require_encryption = no
Sat Jan 25 20:21:59 2014 : Debug:     require_strong = no
Sat Jan 25 20:21:59 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_unix
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sat Jan 25 20:21:59 2014 : Debug:   unix {
Sat Jan 25 20:21:59 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_eap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sat Jan 25 20:21:59 2014 : Debug:   eap {
Sat Jan 25 20:21:59 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:21:59 2014 : Debug:     timer_expire = 60
Sat Jan 25 20:21:59 2014 : Debug:     ignore_unknown_eap_types = no
Sat Jan 25 20:21:59 2014 : Debug:     cisco_accounting_username_bug = no
Sat Jan 25 20:21:59 2014 : Debug:     max_sessions = 4096
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-md5
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-leap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-gtc
Sat Jan 25 20:21:59 2014 : Debug:    gtc {
Sat Jan 25 20:21:59 2014 : Debug:     challenge = "Password: "
Sat Jan 25 20:21:59 2014 : Debug:     auth_type = "PAP"
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-tls
Sat Jan 25 20:21:59 2014 : Debug:    tls {
Sat Jan 25 20:21:59 2014 : Debug:     rsa_key_exchange = no
Sat Jan 25 20:21:59 2014 : Debug:     dh_key_exchange = yes
Sat Jan 25 20:21:59 2014 : Debug:     rsa_key_length = 512
Sat Jan 25 20:21:59 2014 : Debug:     dh_key_length = 512
Sat Jan 25 20:21:59 2014 : Debug:     verify_depth = 0
Sat Jan 25 20:21:59 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sat Jan 25 20:21:59 2014 : Debug:     pem_file_type = yes
Sat Jan 25 20:21:59 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sat Jan 25 20:21:59 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sat Jan 25 20:21:59 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sat Jan 25 20:21:59 2014 : Debug:     private_key_password = "whatever"
Sat Jan 25 20:21:59 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sat Jan 25 20:21:59 2014 : Debug:     random_file = "/dev/urandom"
Sat Jan 25 20:21:59 2014 : Debug:     fragment_size = 1024
Sat Jan 25 20:21:59 2014 : Debug:     include_length = yes
Sat Jan 25 20:21:59 2014 : Debug:     check_crl = no
Sat Jan 25 20:21:59 2014 : Debug:     cipher_list = "DEFAULT"
Sat Jan 25 20:21:59 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sat Jan 25 20:21:59 2014 : Debug:     cache {
Sat Jan 25 20:21:59 2014 : Debug:     enable = no
Sat Jan 25 20:21:59 2014 : Debug:     lifetime = 24
Sat Jan 25 20:21:59 2014 : Debug:     max_entries = 255
Sat Jan 25 20:21:59 2014 : Debug:     }
Sat Jan 25 20:21:59 2014 : Debug:     verify {
Sat Jan 25 20:21:59 2014 : Debug:     }
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-ttls
Sat Jan 25 20:21:59 2014 : Debug:    ttls {
Sat Jan 25 20:21:59 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 20:21:59 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:21:59 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:21:59 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:21:59 2014 : Debug:     include_length = yes
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-peap
Sat Jan 25 20:21:59 2014 : Debug:    peap {
Sat Jan 25 20:21:59 2014 : Debug:     default_eap_type = "mschapv2"
Sat Jan 25 20:21:59 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 20:21:59 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 20:21:59 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sat Jan 25 20:21:59 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating eap-mschapv2
Sat Jan 25 20:21:59 2014 : Debug:    mschapv2 {
Sat Jan 25 20:21:59 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:21:59 2014 : Debug:    }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_realm
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sat Jan 25 20:21:59 2014 : Debug:   realm suffix {
Sat Jan 25 20:21:59 2014 : Debug:     format = "suffix"
Sat Jan 25 20:21:59 2014 : Debug:     delimiter = "@"
Sat Jan 25 20:21:59 2014 : Debug:     ignore_default = no
Sat Jan 25 20:21:59 2014 : Debug:     ignore_null = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_files
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sat Jan 25 20:21:59 2014 : Debug:   files {
Sat Jan 25 20:21:59 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sat Jan 25 20:21:59 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sat Jan 25 20:21:59 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sat Jan 25 20:21:59 2014 : Debug:     compat = "no"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_radutmp
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sat Jan 25 20:21:59 2014 : Debug:   radutmp {
Sat Jan 25 20:21:59 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sat Jan 25 20:21:59 2014 : Debug:     username = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:     case_sensitive = yes
Sat Jan 25 20:21:59 2014 : Debug:     check_with_nas = yes
Sat Jan 25 20:21:59 2014 : Debug:     perm = 384
Sat Jan 25 20:21:59 2014 : Debug:     callerid = yes
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "attr_filter.access_reject" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:21:59 2014 : Debug:   attr_filter attr_filter.access_reject {
Sat Jan 25 20:21:59 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sat Jan 25 20:21:59 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  } # modules
Sat Jan 25 20:21:59 2014 : Debug: } # server
Sat Jan 25 20:21:59 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sat Jan 25 20:21:59 2014 : Debug:  modules {
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_digest
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_preprocess
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sat Jan 25 20:21:59 2014 : Debug:   preprocess {
Sat Jan 25 20:21:59 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sat Jan 25 20:21:59 2014 : Debug:     hints = "/etc/freeradius/hints"
Sat Jan 25 20:21:59 2014 : Debug:     with_ascend_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     ascend_channels_per_line = 23
Sat Jan 25 20:21:59 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     with_specialix_jetstream_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     with_cisco_vsa_hack = no
Sat Jan 25 20:21:59 2014 : Debug:     with_alvarion_vsa_hack = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_sql
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sat Jan 25 20:21:59 2014 : Debug:   sql {
Sat Jan 25 20:21:59 2014 : Debug:     driver = "rlm_sql_mysql"
Sat Jan 25 20:21:59 2014 : Debug:     server = "localhost"
Sat Jan 25 20:21:59 2014 : Debug:     port = ""
Sat Jan 25 20:21:59 2014 : Debug:     login = "radius"
Sat Jan 25 20:21:59 2014 : Debug:     password = "radpass"
Sat Jan 25 20:21:59 2014 : Debug:     radius_db = "radius"
Sat Jan 25 20:21:59 2014 : Debug:     read_groups = yes
Sat Jan 25 20:21:59 2014 : Debug:     sqltrace = no
Sat Jan 25 20:21:59 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sat Jan 25 20:21:59 2014 : Debug:     readclients = no
Sat Jan 25 20:21:59 2014 : Debug:     deletestalesessions = yes
Sat Jan 25 20:21:59 2014 : Debug:     num_sql_socks = 5
Sat Jan 25 20:21:59 2014 : Debug:     lifetime = 0
Sat Jan 25 20:21:59 2014 : Debug:     max_queries = 0
Sat Jan 25 20:21:59 2014 : Debug:     sql_user_name = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:     default_user_profile = ""
Sat Jan 25 20:21:59 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_check_query = "SELECT  id, username, attribute, value, op           FROM radcheck            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_reply_query = "SELECT  id, username, attribute, value, op           FROM radreply            WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_group_check_query =  "SELECT id, groupname, attribute,           Value, op           FROM  radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:21:59 2014 : Debug:     authorize_group_reply_query =  "SELECT id, groupname, attribute,           value, op           FROM  radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER  BY id"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_onoff_query = "           UPDATE radacct           SET              acctstoptime       =  '%S',               acctsessiontime    =  unix_timestamp('%S') -                                     unix_timestamp(acctstarttime),               acctterminatecause =  '%{Acct-Terminate-Cause}',               acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE  acctstoptime IS NULL           AND nasipaddress      =   '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_update_query = "            UPDATE radacct           SET              framedipaddress =  '%{Framed-IP-Address}',              acctsessiontime     =  '%{Acct-Session-Time}',              acctinputoctets     =  '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                     '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets     = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                     '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username        =  '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_update_query_alt = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,       username,              realm,            nasipaddress,       nasportid,              nasporttype,      acctstarttime,      acctsessiontime,              acctauthentic,    connectinfo_start,  acctinputoctets,              acctoutputoctets, calledstationid,    callingstationid,              servicetype,      framedprotocol,     framedipaddress,              acctstartdelay,   xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                        INTERVAL (%{%{Acct-Session-Time}:-0} +                                  %{%{Acct-Delay-Time}:-0}) SECOND),                        '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',               '%{%{Acct-Input-Gigawords}:-0}' << 32 |               '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Service-Type}',  '%{Framed-Protocol}',              '%{Framed-IP-Address}',               '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_start_query = "            INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,     nasportid,               nasporttype,      acctstarttime,    acctstoptime,               acctsessiontime,  acctauthentic,    connectinfo_start,               connectinfo_stop, acctinputoctets,  acctoutputoctets,               calledstationid,  callingstationid, acctterminatecause,               servicetype,      framedprotocol,   framedipaddress,               acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)            VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',               '%{SQL-User-Name}',              '%{Realm}',  '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',  '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',               '', '0', '0',              '%{Called-Station-Id}',  '%{Calling-Station-Id}', '',              '%{Service-Type}',  '%{Framed-Protocol}', '%{Framed-IP-Address}',               '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_start_query_alt = "            UPDATE radacct SET              acctstarttime     = '%S',               acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',               connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  =  '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'            AND nasipaddress     = '%{NAS-IP-Address}'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_stop_query = "            UPDATE radacct SET              acctstoptime       = '%S',               acctsessiontime    = '%{Acct-Session-Time}',               acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Input-Octets}:-0}',               acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}',               acctterminatecause = '%{Acct-Terminate-Cause}',               acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',               connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   =  '%{Acct-Session-Id}'           AND username          =  '%{SQL-User-Name}'           AND nasipaddress      =  '%{NAS-IP-Address}'"
Sat Jan 25 20:21:59 2014 : Debug:     accounting_stop_query_alt = "            INSERT INTO radacct             (acctsessionid, acctuniqueid,  username,              realm, nasipaddress, nasportid,               nasporttype, acctstarttime, acctstoptime,              acctsessiontime,  acctauthentic, connectinfo_start,              connectinfo_stop,  acctinputoctets, acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,  framedprotocol, framedipaddress,              acctstartdelay,  acctstopdelay)           VALUES             ('%{Acct-Session-Id}',  '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',               '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',               '%{NAS-Port-Type}',              DATE_SUB('%S',                   INTERVAL (%{%{Acct-Session-Time}:-0} +                   %{%{Acct-Delay-Time}:-0}) SECOND),              '%S',  '%{Acct-Session-Time}', '%{Acct-Authentic}', '',               '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' <<  32 |              '%{%{Acct-Input-Octets}:-0}',               '%{%{Acct-Output-Gigawords}:-0}' << 32 |               '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}',  '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',               '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',               '0', '%{%{Acct-Delay-Time}:-0}')"
Sat Jan 25 20:21:59 2014 : Debug:     group_membership_query = "SELECT  groupname           FROM radusergroup           WHERE username =  '%{SQL-User-Name}'           ORDER BY priority"
Sat Jan 25 20:21:59 2014 : Debug:     connect_failure_retry_delay = 60
Sat Jan 25 20:21:59 2014 : Debug:     simul_count_query = ""
Sat Jan 25 20:21:59 2014 : Debug:     simul_verify_query = "SELECT  radacctid, acctsessionid, username,                                 nasipaddress, nasportid, framedipaddress,                                 callingstationid, framedprotocol                                FROM  radacct                                WHERE username =  '%{SQL-User-Name}'                                AND acctstoptime IS  NULL"
Sat Jan 25 20:21:59 2014 : Debug:     postauth_query = "INSERT INTO  radpostauth                           (username, pass, reply, authdate)                            VALUES (                            '%{User-Name}',                            '%{%{User-Password}:-%{Chap-Password}}',                            '%{reply:razz:acket-Type}', '%S')"
Sat Jan 25 20:21:59 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 20:21:59 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 20:21:59 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 20:21:59 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 20:21:59 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 20:21:59 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Sat Jan 25 20:21:59 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 20:21:59 2014 : Debug: rlm_sql (sql): Failed to connect to any SQL server.
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sat Jan 25 20:21:59 2014 : Debug:   acct_unique {
Sat Jan 25 20:21:59 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sat Jan 25 20:21:59 2014 : Debug:  Module: Linked to module rlm_detail
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sat Jan 25 20:21:59 2014 : Debug:   detail {
Sat Jan 25 20:21:59 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sat Jan 25 20:21:59 2014 : Debug:     header = "%t"
Sat Jan 25 20:21:59 2014 : Debug:     detailperm = 384
Sat Jan 25 20:21:59 2014 : Debug:     dirperm = 493
Sat Jan 25 20:21:59 2014 : Debug:     locking = no
Sat Jan 25 20:21:59 2014 : Debug:     log_packet_header = no
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Instantiating module  "attr_filter.accounting_response" from file  /etc/freeradius/modules/attr_filter
Sat Jan 25 20:21:59 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sat Jan 25 20:21:59 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sat Jan 25 20:21:59 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 20:21:59 2014 : Debug:   }
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 20:21:59 2014 : Debug:  } # modules
Sat Jan 25 20:21:59 2014 : Debug: } # server
Sat Jan 25 20:21:59 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sat Jan 25 20:21:59 2014 : Debug: listen {
Sat Jan 25 20:21:59 2014 : Debug:     type = "auth"
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = *
Sat Jan 25 20:21:59 2014 : Debug:     port = 0
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: listen {
Sat Jan 25 20:21:59 2014 : Debug:     type = "acct"
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = *
Sat Jan 25 20:21:59 2014 : Debug:     port = 0
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: listen {
Sat Jan 25 20:21:59 2014 : Debug:     type = "auth"
Sat Jan 25 20:21:59 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 20:21:59 2014 : Debug:     port = 18120
Sat Jan 25 20:21:59 2014 : Debug: }
Sat Jan 25 20:21:59 2014 : Debug: Listening on authentication address * port 1812
Sat Jan 25 20:21:59 2014 : Debug: Listening on accounting address * port 1813
Sat Jan 25 20:21:59 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sat Jan 25 20:21:59 2014 : Debug: Listening on proxy address * port 1814
Sat Jan 25 20:21:59 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 48863, id=148, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0x2a7f51cdc0487d4d306f642809d88b35
    CHAP-Password = 0x009c7ea5944ab7aaa1812e93ca907a492e
    Service-Type = Login-User
    Acct-Session-Id = "52e400ae00000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x28137849b1e1e0c80a83bed203f625f5
Sat Jan 25 20:22:30 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:30 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:22:30 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:22:30 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:22:30 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:22:30 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:22:30 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:22:30 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 20:22:30 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:22:30 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:22:30 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:22:30 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:22:30 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:22:30 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:22:30 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:22:30 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:22:30 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:22:30 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:22:30 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:30 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:22:30 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 20:22:30 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:22:30 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:22:30 2014 : Info: Delaying reject of request 0 for 1 seconds
Sat Jan 25 20:22:30 2014 : Debug: Going to the next request
Sat Jan 25 20:22:30 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:22:31 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 148 to 127.0.0.1 port 48863
Sat Jan 25 20:22:31 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:22:36 2014 : Info: Cleaning up request 0 ID 148 with timestamp +31
Sat Jan 25 20:22:36 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 53601, id=153, length=289
    ChilliSpot-Version = "1.2.9"
    User-Name = "lennon"
    CHAP-Challenge = 0x1f266e3bb2a51ebee4de6f7ce04ce257
    CHAP-Password = 0x00aa3b1325a1333f7a3099847ccbe938d2
    Service-Type = Login-User
    Acct-Session-Id = "52e400e700000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0xa8771744d6c0a8fc0c58eee38f0b344b
Sat Jan 25 20:22:45 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:45 2014 : Info: +- entering group authorize {...}
Sat Jan 25 20:22:45 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 20:22:45 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 20:22:45 2014 : Info: ++[chap] returns ok
Sat Jan 25 20:22:45 2014 : Info: ++[mschap] returns noop
Sat Jan 25 20:22:45 2014 : Info: ++[digest] returns noop
Sat Jan 25 20:22:45 2014 : Info: [suffix] No '@' in User-Name = "lennon", looking up realm NULL
Sat Jan 25 20:22:45 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 20:22:45 2014 : Info: ++[suffix] returns noop
Sat Jan 25 20:22:45 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 20:22:45 2014 : Info: ++[eap] returns noop
Sat Jan 25 20:22:45 2014 : Info: [sql]     expand: %{User-Name} -> lennon
Sat Jan 25 20:22:45 2014 : Info: [sql] sql_set_user escaped user --> 'lennon'
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Sat Jan 25 20:22:45 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Sat Jan 25 20:22:45 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 0
Sat Jan 25 20:22:45 2014 : Info: ++[sql] returns fail
Sat Jan 25 20:22:45 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 20:22:45 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 20:22:45 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 20:22:45 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> lennon
Sat Jan 25 20:22:45 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 20:22:45 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 20:22:45 2014 : Info: Delaying reject of request 1 for 1 seconds
Sat Jan 25 20:22:45 2014 : Debug: Going to the next request
Sat Jan 25 20:22:45 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 20:22:46 2014 : Info: Sending delayed reject for request 1
Sending Access-Reject of id 153 to 127.0.0.1 port 53601
Sat Jan 25 20:22:46 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 20:22:51 2014 : Info: Cleaning up request 1 ID 153 with timestamp +46
Sat Jan 25 20:22:51 2014 : Info: Ready to process requests.
 
```


my /etc/network/interfaces is as follows:

```
 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        gateway 192.168.2.1
        dns-nameservers 208.67.222.222 208.67.220.220


iface eth1 inet dhcp
        address 10.1.0.1
        netmask 255.255.255.0
        gateway 192.168.2.1
        dns-nameservers 10.1.0.1



```

compressed file of the directory /etc/freeradius
[ATTACH]249742[/ATTACH]


Apologies if i have not posted my question in a standard way, been looking for the instructions on how to post correctly, but cannot find them!

I noticed i had the error 
```
Sat Jan 25 22:57:09 2014 : Debug:   }
Sat Jan 25 22:57:09 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 22:57:09 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 22:57:09 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 22:57:09 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 22:57:09 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 22:57:09 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' to database 'radius''
Sat Jan 25 22:57:09 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): Failed to connect to any SQL server.
 
```
 when running 
```
#freeradius -XXX
```

I checked my mysql database using 
```
#mysql -u root -p
mysql> show databases;
 
```
which revealed that there is no database called 'radius'. 

I then created the databse radius as follows:
```
# [FONT=&amp]  mysql -u root -p[/FONT]
  [FONT=&amp]mysql> create database radius;[/FONT]
  [FONT=&amp]mysql>quit[/FONT]
```
then
```
#cd /var/www/daloradius/contrib/db/
# mysql -u root -p radius < fr2-mysql-daloradius-and-freeradius.sql 
#[FONT=&amp]  mysql -u root -p
[/FONT] 
```
At this point, as the user 'radius' was already there (by what means, i am not sure, since the instructions say nothing about creating a user 'radius', i don't even know what password it's using), i simply granted privileges to that user:
```
   [FONT=&amp]mysql>GRANT ALL PRIVILEGES ON radius.* to 'radius'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> quit;
[/FONT] 
```

I then ran
```
#freeradius -XXX
``` 
again, and this time, the output showed 
```
Sat Jan 25 22:59:44 2014 : Debug:   }
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
 
```

The full output of is as follows: 
```
root@ubuntu:~# freeradius -XXX
Sat Jan 25 23:21:31 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sat Jan 25 23:21:31 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sat Jan 25 23:21:31 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sat Jan 25 23:21:31 2014 : Info: PARTICULAR PURPOSE. 
Sat Jan 25 23:21:31 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sat Jan 25 23:21:31 2014 : Info: GNU General Public License v2. 
Sat Jan 25 23:21:31 2014 : Info: Starting - reading configuration files ...
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sat Jan 25 23:21:31 2014 : Debug: including files in directory /etc/freeradius/modules/
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sat Jan 25 23:21:31 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 23:21:31 2014 : Debug: main {
Sat Jan 25 23:21:31 2014 : Debug:     user = "freerad"
Sat Jan 25 23:21:31 2014 : Debug:     group = "freerad"
Sat Jan 25 23:21:31 2014 : Debug:     allow_core_dumps = no
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sat Jan 25 23:21:31 2014 : Debug: main {
Sat Jan 25 23:21:31 2014 : Debug:     prefix = "/usr"
Sat Jan 25 23:21:31 2014 : Debug:     localstatedir = "/var"
Sat Jan 25 23:21:31 2014 : Debug:     logdir = "/var/log/freeradius"
Sat Jan 25 23:21:31 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sat Jan 25 23:21:31 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sat Jan 25 23:21:31 2014 : Debug:     hostname_lookups = no
Sat Jan 25 23:21:31 2014 : Debug:     max_request_time = 30
Sat Jan 25 23:21:31 2014 : Debug:     cleanup_delay = 5
Sat Jan 25 23:21:31 2014 : Debug:     max_requests = 1024
Sat Jan 25 23:21:31 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sat Jan 25 23:21:31 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sat Jan 25 23:21:31 2014 : Debug:     debug_level = 0
Sat Jan 25 23:21:31 2014 : Debug:     proxy_requests = yes
Sat Jan 25 23:21:31 2014 : Debug:  log {
Sat Jan 25 23:21:31 2014 : Debug:     stripped_names = no
Sat Jan 25 23:21:31 2014 : Debug:     auth = no
Sat Jan 25 23:21:31 2014 : Debug:     auth_badpass = no
Sat Jan 25 23:21:31 2014 : Debug:     auth_goodpass = no
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  security {
Sat Jan 25 23:21:31 2014 : Debug:     max_attributes = 200
Sat Jan 25 23:21:31 2014 : Debug:     reject_delay = 1
Sat Jan 25 23:21:31 2014 : Debug:     status_server = yes
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sat Jan 25 23:21:31 2014 : Debug:  proxy server {
Sat Jan 25 23:21:31 2014 : Debug:     retry_delay = 5
Sat Jan 25 23:21:31 2014 : Debug:     retry_count = 3
Sat Jan 25 23:21:31 2014 : Debug:     default_fallback = no
Sat Jan 25 23:21:31 2014 : Debug:     dead_time = 120
Sat Jan 25 23:21:31 2014 : Debug:     wake_all_if_all_dead = no
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  home_server localhost {
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 23:21:31 2014 : Debug:     port = 1812
Sat Jan 25 23:21:31 2014 : Debug:     type = "auth"
Sat Jan 25 23:21:31 2014 : Debug:     secret = "testing123"
Sat Jan 25 23:21:31 2014 : Debug:     response_window = 20
Sat Jan 25 23:21:31 2014 : Debug:     max_outstanding = 65536
Sat Jan 25 23:21:31 2014 : Debug:     require_message_authenticator = yes
Sat Jan 25 23:21:31 2014 : Debug:     zombie_period = 40
Sat Jan 25 23:21:31 2014 : Debug:     status_check = "status-server"
Sat Jan 25 23:21:31 2014 : Debug:     ping_interval = 30
Sat Jan 25 23:21:31 2014 : Debug:     check_interval = 30
Sat Jan 25 23:21:31 2014 : Debug:     num_answers_to_alive = 3
Sat Jan 25 23:21:31 2014 : Debug:     num_pings_to_alive = 3
Sat Jan 25 23:21:31 2014 : Debug:     revive_interval = 120
Sat Jan 25 23:21:31 2014 : Debug:     status_check_timeout = 4
Sat Jan 25 23:21:31 2014 : Debug:     irt = 2
Sat Jan 25 23:21:31 2014 : Debug:     mrt = 16
Sat Jan 25 23:21:31 2014 : Debug:     mrc = 5
Sat Jan 25 23:21:31 2014 : Debug:     mrd = 30
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  home_server_pool my_auth_failover {
Sat Jan 25 23:21:31 2014 : Debug:     type = fail-over
Sat Jan 25 23:21:31 2014 : Debug:     home_server = localhost
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  realm example.com {
Sat Jan 25 23:21:31 2014 : Debug:     auth_pool = my_auth_failover
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  realm LOCAL {
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Loading Clients ####
Sat Jan 25 23:21:31 2014 : Debug:  client localhost {
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 23:21:31 2014 : Debug:     require_message_authenticator = no
Sat Jan 25 23:21:31 2014 : Debug:     secret = "testing123"
Sat Jan 25 23:21:31 2014 : Debug:     nastype = "other"
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Instantiating modules ####
Sat Jan 25 23:21:31 2014 : Debug:  instantiate {
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_exec
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sat Jan 25 23:21:31 2014 : Debug:   exec {
Sat Jan 25 23:21:31 2014 : Debug:     wait = no
Sat Jan 25 23:21:31 2014 : Debug:     input_pairs = "request"
Sat Jan 25 23:21:31 2014 : Debug:     shell_escape = yes
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 23:21:31 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sat Jan 25 23:21:31 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 23:21:31 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 23:21:31 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 23:21:31 2014 : Debug:     key = "User-Name"
Sat Jan 25 23:21:31 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 23:21:31 2014 : Debug:     query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 23:21:31 2014 : Debug:     reset = "never"
Sat Jan 25 23:21:31 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Next reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Prev reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 23:21:31 2014 : Debug:   sqlcounter noresetcounter {
Sat Jan 25 23:21:31 2014 : Debug:     counter-name = "Session-Timeout"
Sat Jan 25 23:21:31 2014 : Debug:     check-name = "Session-Timeout"
Sat Jan 25 23:21:31 2014 : Debug:     reply-name = "Session-Timeout"
Sat Jan 25 23:21:31 2014 : Debug:     key = "User-Name"
Sat Jan 25 23:21:31 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 23:21:31 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 23:21:31 2014 : Debug:     reset = "never"
Sat Jan 25 23:21:31 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Next reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Prev reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_expr
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_expiration
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sat Jan 25 23:21:31 2014 : Debug:   expiration {
Sat Jan 25 23:21:31 2014 : Debug:     reply-message = "Password Has Expired  "
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_logintime
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sat Jan 25 23:21:31 2014 : Debug:   logintime {
Sat Jan 25 23:21:31 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sat Jan 25 23:21:31 2014 : Debug:     minimum-timeout = 60
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sat Jan 25 23:21:31 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 23:21:31 2014 : Debug:  modules {
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_pap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sat Jan 25 23:21:31 2014 : Debug:   pap {
Sat Jan 25 23:21:31 2014 : Debug:     encryption_scheme = "auto"
Sat Jan 25 23:21:31 2014 : Debug:     auto_header = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_chap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_mschap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sat Jan 25 23:21:31 2014 : Debug:   mschap {
Sat Jan 25 23:21:31 2014 : Debug:     use_mppe = yes
Sat Jan 25 23:21:31 2014 : Debug:     require_encryption = no
Sat Jan 25 23:21:31 2014 : Debug:     require_strong = no
Sat Jan 25 23:21:31 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_unix
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sat Jan 25 23:21:31 2014 : Debug:   unix {
Sat Jan 25 23:21:31 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_eap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sat Jan 25 23:21:31 2014 : Debug:   eap {
Sat Jan 25 23:21:31 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 23:21:31 2014 : Debug:     timer_expire = 60
Sat Jan 25 23:21:31 2014 : Debug:     ignore_unknown_eap_types = no
Sat Jan 25 23:21:31 2014 : Debug:     cisco_accounting_username_bug = no
Sat Jan 25 23:21:31 2014 : Debug:     max_sessions = 4096
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-md5
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-leap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-gtc
Sat Jan 25 23:21:31 2014 : Debug:    gtc {
Sat Jan 25 23:21:31 2014 : Debug:     challenge = "Password: "
Sat Jan 25 23:21:31 2014 : Debug:     auth_type = "PAP"
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-tls
Sat Jan 25 23:21:31 2014 : Debug:    tls {
Sat Jan 25 23:21:31 2014 : Debug:     rsa_key_exchange = no
Sat Jan 25 23:21:31 2014 : Debug:     dh_key_exchange = yes
Sat Jan 25 23:21:31 2014 : Debug:     rsa_key_length = 512
Sat Jan 25 23:21:31 2014 : Debug:     dh_key_length = 512
Sat Jan 25 23:21:31 2014 : Debug:     verify_depth = 0
Sat Jan 25 23:21:31 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sat Jan 25 23:21:31 2014 : Debug:     pem_file_type = yes
Sat Jan 25 23:21:31 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sat Jan 25 23:21:31 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sat Jan 25 23:21:31 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sat Jan 25 23:21:31 2014 : Debug:     private_key_password = "whatever"
Sat Jan 25 23:21:31 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sat Jan 25 23:21:31 2014 : Debug:     random_file = "/dev/urandom"
Sat Jan 25 23:21:31 2014 : Debug:     fragment_size = 1024
Sat Jan 25 23:21:31 2014 : Debug:     include_length = yes
Sat Jan 25 23:21:31 2014 : Debug:     check_crl = no
Sat Jan 25 23:21:31 2014 : Debug:     cipher_list = "DEFAULT"
Sat Jan 25 23:21:31 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sat Jan 25 23:21:31 2014 : Debug:     cache {
Sat Jan 25 23:21:31 2014 : Debug:     enable = no
Sat Jan 25 23:21:31 2014 : Debug:     lifetime = 24
Sat Jan 25 23:21:31 2014 : Debug:     max_entries = 255
Sat Jan 25 23:21:31 2014 : Debug:     }
Sat Jan 25 23:21:31 2014 : Debug:     verify {
Sat Jan 25 23:21:31 2014 : Debug:     }
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-ttls
Sat Jan 25 23:21:31 2014 : Debug:    ttls {
Sat Jan 25 23:21:31 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 23:21:31 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 23:21:31 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 23:21:31 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 23:21:31 2014 : Debug:     include_length = yes
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-peap
Sat Jan 25 23:21:31 2014 : Debug:    peap {
Sat Jan 25 23:21:31 2014 : Debug:     default_eap_type = "mschapv2"
Sat Jan 25 23:21:31 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 23:21:31 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 23:21:31 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sat Jan 25 23:21:31 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-mschapv2
Sat Jan 25 23:21:31 2014 : Debug:    mschapv2 {
Sat Jan 25 23:21:31 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_realm
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sat Jan 25 23:21:31 2014 : Debug:   realm suffix {
Sat Jan 25 23:21:31 2014 : Debug:     format = "suffix"
Sat Jan 25 23:21:31 2014 : Debug:     delimiter = "@"
Sat Jan 25 23:21:31 2014 : Debug:     ignore_default = no
Sat Jan 25 23:21:31 2014 : Debug:     ignore_null = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_files
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sat Jan 25 23:21:31 2014 : Debug:   files {
Sat Jan 25 23:21:31 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sat Jan 25 23:21:31 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sat Jan 25 23:21:31 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sat Jan 25 23:21:31 2014 : Debug:     compat = "no"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_radutmp
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sat Jan 25 23:21:31 2014 : Debug:   radutmp {
Sat Jan 25 23:21:31 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sat Jan 25 23:21:31 2014 : Debug:     username = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:     case_sensitive = yes
Sat Jan 25 23:21:31 2014 : Debug:     check_with_nas = yes
Sat Jan 25 23:21:31 2014 : Debug:     perm = 384
Sat Jan 25 23:21:31 2014 : Debug:     callerid = yes
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Sat Jan 25 23:21:31 2014 : Debug:   attr_filter attr_filter.access_reject {
Sat Jan 25 23:21:31 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sat Jan 25 23:21:31 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  } # modules
Sat Jan 25 23:21:31 2014 : Debug: } # server
Sat Jan 25 23:21:31 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sat Jan 25 23:21:31 2014 : Debug:  modules {
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_digest
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_preprocess
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sat Jan 25 23:21:31 2014 : Debug:   preprocess {
Sat Jan 25 23:21:31 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sat Jan 25 23:21:31 2014 : Debug:     hints = "/etc/freeradius/hints"
Sat Jan 25 23:21:31 2014 : Debug:     with_ascend_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     ascend_channels_per_line = 23
Sat Jan 25 23:21:31 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     with_specialix_jetstream_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     with_cisco_vsa_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     with_alvarion_vsa_hack = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_sql
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sat Jan 25 23:21:31 2014 : Debug:   sql {
Sat Jan 25 23:21:31 2014 : Debug:     driver = "rlm_sql_mysql"
Sat Jan 25 23:21:31 2014 : Debug:     server = "localhost"
Sat Jan 25 23:21:31 2014 : Debug:     port = ""
Sat Jan 25 23:21:31 2014 : Debug:     login = "radius"
Sat Jan 25 23:21:31 2014 : Debug:     password = "radpass"
Sat Jan 25 23:21:31 2014 : Debug:     radius_db = "radius"
Sat Jan 25 23:21:31 2014 : Debug:     read_groups = yes
Sat Jan 25 23:21:31 2014 : Debug:     sqltrace = no
Sat Jan 25 23:21:31 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sat Jan 25 23:21:31 2014 : Debug:     readclients = no
Sat Jan 25 23:21:31 2014 : Debug:     deletestalesessions = yes
Sat Jan 25 23:21:31 2014 : Debug:     num_sql_socks = 5
Sat Jan 25 23:21:31 2014 : Debug:     lifetime = 0
Sat Jan 25 23:21:31 2014 : Debug:     max_queries = 0
Sat Jan 25 23:21:31 2014 : Debug:     sql_user_name = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:     default_user_profile = ""
Sat Jan 25 23:21:31 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_check_query = "SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_reply_query = "SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_group_check_query = "SELECT id, groupname, attribute,           Value, op           FROM radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_group_reply_query = "SELECT id, groupname, attribute,           value, op           FROM radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_onoff_query = "          UPDATE radacct           SET              acctstoptime       =  '%S',              acctsessiontime    =  unix_timestamp('%S') -                                    unix_timestamp(acctstarttime),              acctterminatecause =  '%{Acct-Terminate-Cause}',              acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE acctstoptime IS NULL           AND nasipaddress      =  '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_update_query = "           UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_update_query_alt = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,      nasportid,              nasporttype,      acctstarttime,     acctsessiontime,              acctauthentic,    connectinfo_start, acctinputoctets,              acctoutputoctets, calledstationid,   callingstationid,              servicetype,      framedprotocol,    framedipaddress,              acctstartdelay,   xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                       INTERVAL (%{%{Acct-Session-Time}:-0} +                                 %{%{Acct-Delay-Time}:-0}) SECOND),                       '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Service-Type}', '%{Framed-Protocol}',              '%{Framed-IP-Address}',              '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_start_query = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,     username,              realm,            nasipaddress,     nasportid,              nasporttype,      acctstarttime,    acctstoptime,              acctsessiontime,  acctauthentic,    connectinfo_start,              connectinfo_stop, acctinputoctets,  acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,      framedprotocol,   framedipaddress,              acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}', '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',              '', '0', '0',              '%{Called-Station-Id}', '%{Calling-Station-Id}', '',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_start_query_alt = "           UPDATE radacct SET              acctstarttime     = '%S',              acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',              connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'           AND nasipaddress     = '%{NAS-IP-Address}'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_stop_query = "           UPDATE radacct SET              acctstoptime       = '%S',              acctsessiontime    = '%{Acct-Session-Time}',              acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Output-Octets}:-0}',              acctterminatecause = '%{Acct-Terminate-Cause}',              acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',              connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   = '%{Acct-Session-Id}'           AND username          = '%{SQL-User-Name}'           AND nasipaddress      = '%{NAS-IP-Address}'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_stop_query_alt = "           INSERT INTO radacct             (acctsessionid, acctuniqueid, username,              realm, nasipaddress, nasportid,              nasporttype, acctstarttime, acctstoptime,              acctsessiontime, acctauthentic, connectinfo_start,              connectinfo_stop, acctinputoctets, acctoutputoctets,              calledstationid, callingstationid, acctterminatecause,              servicetype, framedprotocol, framedipaddress,              acctstartdelay, acctstopdelay)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                  INTERVAL (%{%{Acct-Session-Time}:-0} +                  %{%{Acct-Delay-Time}:-0}) SECOND),              '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '',              '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '0', '%{%{Acct-Delay-Time}:-0}')"
Sat Jan 25 23:21:31 2014 : Debug:     group_membership_query = "SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority"
Sat Jan 25 23:21:31 2014 : Debug:     connect_failure_retry_delay = 60
Sat Jan 25 23:21:31 2014 : Debug:     simul_count_query = ""
Sat Jan 25 23:21:31 2014 : Debug:     simul_verify_query = "SELECT radacctid, acctsessionid, username,                                nasipaddress, nasportid, framedipaddress,                                callingstationid, framedprotocol                                FROM radacct                                WHERE username = '%{SQL-User-Name}'                                AND acctstoptime IS NULL"
Sat Jan 25 23:21:31 2014 : Debug:     postauth_query = "INSERT INTO radpostauth                           (username, pass, reply, authdate)                           VALUES (                           '%{User-Name}',                           '%{%{User-Password}:-%{Chap-Password}}',                           '%{reply:Packet-Type}', '%S')"
Sat Jan 25 23:21:31 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sat Jan 25 23:21:31 2014 : Debug:   acct_unique {
Sat Jan 25 23:21:31 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_detail
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sat Jan 25 23:21:31 2014 : Debug:   detail {
Sat Jan 25 23:21:31 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sat Jan 25 23:21:31 2014 : Debug:     header = "%t"
Sat Jan 25 23:21:31 2014 : Debug:     detailperm = 384
Sat Jan 25 23:21:31 2014 : Debug:     dirperm = 493
Sat Jan 25 23:21:31 2014 : Debug:     locking = no
Sat Jan 25 23:21:31 2014 : Debug:     log_packet_header = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
Sat Jan 25 23:21:31 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sat Jan 25 23:21:31 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sat Jan 25 23:21:31 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  } # modules
Sat Jan 25 23:21:31 2014 : Debug: } # server
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sat Jan 25 23:21:31 2014 : Debug: listen {
Sat Jan 25 23:21:31 2014 : Debug:     type = "auth"
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = *
Sat Jan 25 23:21:31 2014 : Debug:     port = 0
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: listen {
Sat Jan 25 23:21:31 2014 : Debug:     type = "acct"
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = *
Sat Jan 25 23:21:31 2014 : Debug:     port = 0
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: listen {
Sat Jan 25 23:21:31 2014 : Debug:     type = "auth"
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 23:21:31 2014 : Debug:     port = 18120
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: Listening on authentication address * port 1812
Sat Jan 25 23:21:31 2014 : Debug: Listening on accounting address * port 1813
Sat Jan 25 23:21:31 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sat Jan 25 23:21:31 2014 : Debug: Listening on proxy address * port 1814
Sat Jan 25 23:21:31 2014 : Info: Ready to process requests.
 
```

I know creating the database 'radius' isn't part of the instructions, but it has helped resolved the 'Couldn't connect socket to MySQL server' related errors. Am i moving in the right direction in trying to solve my problem? If i am, what can i do next? My comprehension of some of the errors in the debug ding report is limited. Thanks for any help!

edit:

When i try to do a client login, the following is the debug output:
```
 rad_recv: Access-Request packet from host 127.0.0.1 port 37771, id=240, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0xa0a6392520bd9ecd4fd4696505708445
    CHAP-Password = 0x006bc5fa8b1471ba7619f4b8a94ba3c23d
    Service-Type = Login-User
    Acct-Session-Id = "52e425d800000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x399c34b3b1166b663bb267455329830f
Sat Jan 25 23:38:33 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:38:33 2014 : Info: +- entering group authorize {...}
Sat Jan 25 23:38:33 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 23:38:33 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 23:38:33 2014 : Info: ++[chap] returns ok
Sat Jan 25 23:38:33 2014 : Info: ++[mschap] returns noop
Sat Jan 25 23:38:33 2014 : Info: ++[digest] returns noop
Sat Jan 25 23:38:33 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 23:38:33 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 23:38:33 2014 : Info: ++[suffix] returns noop
Sat Jan 25 23:38:33 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 23:38:33 2014 : Info: ++[eap] returns noop
Sat Jan 25 23:38:33 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 23:38:33 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 23:38:33 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 4
Sat Jan 25 23:38:33 2014 : Info: [sql]     expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'omniWezkHeWq'           ORDER BY id
Sat Jan 25 23:38:33 2014 : Info: [sql]     expand: SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority -> SELECT groupname           FROM radusergroup           WHERE username = 'omniWezkHeWq'           ORDER BY priority
Sat Jan 25 23:38:33 2014 : Debug: rlm_sql (sql): Released sql socket id: 4
Sat Jan 25 23:38:33 2014 : Info: [sql] User omniWezkHeWq not found
Sat Jan 25 23:38:33 2014 : Info: ++[sql] returns notfound
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Sat Jan 25 23:38:33 2014 : Info: ++[chillispot_max_bytes] returns noop
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Sat Jan 25 23:38:33 2014 : Info: ++[noresetcounter] returns noop
Sat Jan 25 23:38:33 2014 : Info: ++[expiration] returns noop
Sat Jan 25 23:38:33 2014 : Info: ++[logintime] returns noop
Sat Jan 25 23:38:33 2014 : Info: [pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
Sat Jan 25 23:38:33 2014 : Info: ++[pap] returns noop
Sat Jan 25 23:38:33 2014 : Info: Found Auth-Type = CHAP
Sat Jan 25 23:38:33 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:38:33 2014 : Info: +- entering group CHAP {...}
Sat Jan 25 23:38:33 2014 : Info: [chap] login attempt by "omniWezkHeWq" with CHAP password
Sat Jan 25 23:38:33 2014 : Info: [chap] Cleartext-Password is required for authentication
Sat Jan 25 23:38:33 2014 : Info: ++[chap] returns invalid
Sat Jan 25 23:38:33 2014 : Info: Failed to authenticate the user.
Sat Jan 25 23:38:33 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 23:38:33 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:38:33 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 23:38:33 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 23:38:33 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 23:38:33 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 23:38:33 2014 : Info: Delaying reject of request 0 for 1 seconds
Sat Jan 25 23:38:33 2014 : Debug: Going to the next request
Sat Jan 25 23:38:33 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 23:38:34 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 240 to 127.0.0.1 port 37771
Sat Jan 25 23:38:34 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 23:38:39 2014 : Info: Cleaning up request 0 ID 240 with timestamp +1022
Sat Jan 25 23:38:39 2014 : Info: Ready to process requests.


```

---

### Post by okay7675 on 2014-01-25
> **ahmad7jafari said:**
> hi 
I am use daloradius virtualbox image that run under ubuntu 10.4 LTS and install coova-chilli .
all is good But client have any redirect to login page!
there is my output of chilli debug:
```
root@lamp ~# chilli --fg --debug
main-opt.c: 403: 0 (Debug) DHCP Listen: 192.168.10.208
main-opt.c: 404: 0 (Debug) UAM Listen: 192.168.10.208
garden.c: 62: 0 (Debug) Uamallowed www.coova.org
garden.c: 126: 0 (Debug) Invalid uamallowed domain or address: www.coova.org!
garden.c: 62: 0 (Debug) Uamallowed 192.168.10.208
garden.c: 44: 0 (Debug) Uamallowed IP address #0:512: proto=0 host=192.168.10.208 port=0
garden.c: 62: 0 (Debug) Uamallowed
garden.c: 126: 0 (Debug) Invalid uamallowed domain or address: !
garden.c: 62: 0 (Debug) Uamallowed www.coova.org
garden.c: 126: 0 (Debug) Invalid uamallowed domain or address: www.coova.org!
garden.c: 62: 0 (Debug) Uamallowed 192.168.10.1/255
options.c: 57: 0 (Debug) Invalid mask
garden.c: 115: 0 (Debug) Invalid uamallowed network address or mask 192.168.10.1/255!
options.c: 367: 0 (Debug) PID 1568 saving options to /var/run/chilli.1567.cfg.bin
options.c: 544: 0 (Debug) PID 1567 reloaded binary options file
chilli.c: 4848: 0 (Debug) clock realtime sec 1389509098 nsec 962522139
chilli.c: 4853: 0 (Debug) clock monotonic sec 325 nsec 654157486
tun.c: 520: 0 (Debug) TX queue length set to 100
ippool.c: 322: 0 (Debug) Hashlog 8 253 256

net.c: 1028: 0 (Debug) Net SNDBUF 112640
net.c: 1031: 0 (Debug) Net RCVBUF 112640
net.c: 1083: 0 (Debug) device eth1 ifindex 3
dhcp.c: 208: 0 (Debug) GARP: Replying to broadcast
chilli.c: 5084: 0 (Debug) Waiting for client request...
radius.c: 1423: 0 (Debug) RADIUS to 127.0.0.1:1813
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=08:00:27:50:7f:13 dst=00:11:09:5e:2f:c9 prot=0800 2048 len=234
dhcp.c: 2795: 0 (Debug) Not for our MAC or broadcast: 00-11-09-5E-2F-C9
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=08:00:27:50:7f:13 prot=0800 2048 len=60
dhcp.c: 2795: 0 (Debug) Not for our MAC or broadcast: 08-00-27-50-7F-13
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=08:00:27:50:7f:13 dst=00:11:09:5e:2f:c9 prot=0800 2048 len=106
dhcp.c: 2795: 0 (Debug) Not for our MAC or broadcast: 00-11-09-5E-2F-C9
main-script.c: 75: 0 (Debug) USER root(0/0), GROUP root(0/0) CHILLI[UID 108, GID 112]
main-script.c: 93: 0 (Debug) Running /etc/chilli/up.sh (0/0)
/etc/chilli/up.sh: 64: ./etc/chilli/ipup.sh: not found
chilli.c: 273: 0 (Debug) caught 17 via selfpipe
chilli.c: 232: 0 (Debug) child 1570 terminated
.
.
.
.
.
.
.

dns.c: 182: 0 (Debug) dns_copy_res(left=20 olen=20 qsize=512)
dns.c: 205: 0 (Debug) It was a dns record type: 1 class: 1
dns.c: 39: 0 (Debug) dlen=512 reslen=20 olen=20 lvl=0
dns.c: 73: 0 (Debug) part[www] reslen=19 l=3 dlen=512
dns.c: 73: 0 (Debug) part[google] reslen=15 l=6 dlen=508
dns.c: 73: 0 (Debug) part[com] reslen=8 l=3 dlen=501
dns.c: 234: 0 (Debug) Q: www.google.com
dhcp.c: 1411: 0 (Debug) an: 0
dhcp.c: 1412: 0 (Debug) ns: 0
dhcp.c: 1413: 0 (Debug) ar: 0
dhcp.c: 1415: 0 (Debug) left (should be zero): 0
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=08:00:27:bf:cc:9a prot=0800 2048 len=74
dhcp.c: 1385: 0 (Debug) dhcp_dns plen=74 dlen=20 olen=20
dhcp.c: 1387: 0 (Debug) DNS ID:    31921
dhcp.c: 1388: 0 (Debug) DNS Flags: 256
dhcp.c: 1410: 0 (Debug) qd: 1
dns.c: 182: 0 (Debug) dns_copy_res(left=20 olen=20 qsize=512)
dns.c: 205: 0 (Debug) It was a dns record type: 1 class: 1
dns.c: 39: 0 (Debug) dlen=512 reslen=20 olen=20 lvl=0
dns.c: 73: 0 (Debug) part[www] reslen=19 l=3 dlen=512
dns.c: 73: 0 (Debug) part[google] reslen=15 l=6 dlen=508
dns.c: 73: 0 (Debug) part[com] reslen=8 l=3 dlen=501
dns.c: 234: 0 (Debug) Q: www.google.com
dhcp.c: 1411: 0 (Debug) an: 0
dhcp.c: 1412: 0 (Debug) ns: 0
dhcp.c: 1413: 0 (Debug) ar: 0
dhcp.c: 1415: 0 (Debug) left (should be zero): 0
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=ff:ff:ff:ff:ff:ff prot=0800 2048 len=92
dhcp.c: 2890: 0 (Debug) Broadcasted UDP to port 137
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=ff:ff:ff:ff:ff:ff prot=0800 2048 len=92
dhcp.c: 2890: 0 (Debug) Broadcasted UDP to port 137
dhcp.c: 3420: 0 (Debug) dhcp_decaps: src=00:11:09:5e:2f:c9 dst=ff:ff:ff:ff:ff:ff prot=0800 2048 len=92
dhcp.c: 2890: 0 (Debug) Broadcasted UDP to port 137


```
where:
192.168.10.208 is my lan NIC
192.168.10.206 is my internet NIC
and client winXP get ip:192.168.10.1 from serevr

please help me ......

Hi, can you please post what the **uamallowed **is in /etc/chilli/functions around line 86?

---

### Post by okay7675 on 2014-01-26
I inserted a random user 'randtest' with a password 'randtest' and added it to mysql (the database in use is 'radius')
```
 mysql> insert into radcheck (username, attribute, value) values ('randtest', 'Password', 'randtest');

```
and i can now access the internet using these credentials. Questions:
[LIST=1]
[*]Why? 
[*]Is it that the users that i am generating using the daloradius front end are not being added into radcheck? if so, how do i fix this? 
[*]Is there any accounting thats being 'applied' to this user 'randtest'? Can i restrict bandwidth, time etc? 
[/LIST]

> **okay7675 said:**
> I noticed i had the error 
```
Sat Jan 25 22:57:09 2014 : Debug:   }
Sat Jan 25 22:57:09 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 22:57:09 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 22:57:09 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 22:57:09 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 22:57:09 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Sat Jan 25 22:57:09 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' to database 'radius''
Sat Jan 25 22:57:09 2014 : Error: rlm_sql (sql): Failed to connect DB handle #0
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 22:57:09 2014 : Debug: rlm_sql (sql): Failed to connect to any SQL server.
 
```
 when running 
```
#freeradius -XXX
```

I checked my mysql database using 
```
#mysql -u root -p
mysql> show databases;
 
```
which revealed that there is no database called 'radius'. 

I then created the databse radius as follows:
```
# [FONT=&amp]  mysql -u root -p[/FONT]
  [FONT=&amp]mysql> create database radius;[/FONT]
  [FONT=&amp]mysql>quit[/FONT]
```
then
```
#cd /var/www/daloradius/contrib/db/
# mysql -u root -p radius < fr2-mysql-daloradius-and-freeradius.sql 
#[FONT=&amp]  mysql -u root -p
[/FONT] 
```
At this point, as the user 'radius' was already there (by what means, i am not sure, since the instructions say nothing about creating a user 'radius', i don't even know what password it's using), i simply granted privileges to that user:
```
   [FONT=&amp]mysql>GRANT ALL PRIVILEGES ON radius.* to 'radius'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> quit;
[/FONT] 
```

I then ran
```
#freeradius -XXX
``` 
again, and this time, the output showed 
```
Sat Jan 25 22:59:44 2014 : Debug:   }
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Sat Jan 25 22:59:44 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 22:59:44 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 22:59:44 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
 
```

The full output of is as follows: 
```
root@ubuntu:~# freeradius -XXX
Sat Jan 25 23:21:31 2014 : Info: FreeRADIUS Version 2.1.10, for host i686-pc-linux-gnu, built on Sep 24 2012 at 17:53:32
Sat Jan 25 23:21:31 2014 : Info: Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
Sat Jan 25 23:21:31 2014 : Info: There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
Sat Jan 25 23:21:31 2014 : Info: PARTICULAR PURPOSE. 
Sat Jan 25 23:21:31 2014 : Info: You may redistribute copies of FreeRADIUS under the terms of the 
Sat Jan 25 23:21:31 2014 : Info: GNU General Public License v2. 
Sat Jan 25 23:21:31 2014 : Info: Starting - reading configuration files ...
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/radiusd.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/proxy.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/clients.conf
Sat Jan 25 23:21:31 2014 : Debug: including files in directory /etc/freeradius/modules/
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/pap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/ldap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/counter
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/cui
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/radutmp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/preprocess
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/radrelay
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/replicate
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/unix
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/dynamic_clients
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/ntlm_auth
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/mac2ip
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/always
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/perl
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/sradutmp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/linelog
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/redis
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/opendirectory
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/dhcp_sqlippool
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/expiration
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/acct_unique
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/smsotp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/mac2vlan
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/passwd
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/sql_log
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/mschap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/otp
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/pam
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/digest
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/cache
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/logintime
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/realm
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/echo
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/files
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/inner-eap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/detail.example.com
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/chap
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/expr
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/rediswho
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/ippool
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/attr_filter
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/krb5
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/detail.log
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/wimax
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/detail
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/checkval
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/policy
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/soh
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/attr_rewrite
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/etc_group
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/exec
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/modules/smbpasswd
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/eap.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sql.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/dialup.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/policy.conf
Sat Jan 25 23:21:31 2014 : Debug: including files in directory /etc/freeradius/sites-enabled/
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:21:31 2014 : Debug: including configuration file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 23:21:31 2014 : Debug: main {
Sat Jan 25 23:21:31 2014 : Debug:     user = "freerad"
Sat Jan 25 23:21:31 2014 : Debug:     group = "freerad"
Sat Jan 25 23:21:31 2014 : Debug:     allow_core_dumps = no
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: including dictionary file /etc/freeradius/dictionary
Sat Jan 25 23:21:31 2014 : Debug: main {
Sat Jan 25 23:21:31 2014 : Debug:     prefix = "/usr"
Sat Jan 25 23:21:31 2014 : Debug:     localstatedir = "/var"
Sat Jan 25 23:21:31 2014 : Debug:     logdir = "/var/log/freeradius"
Sat Jan 25 23:21:31 2014 : Debug:     libdir = "/usr/lib/freeradius"
Sat Jan 25 23:21:31 2014 : Debug:     radacctdir = "/var/log/freeradius/radacct"
Sat Jan 25 23:21:31 2014 : Debug:     hostname_lookups = no
Sat Jan 25 23:21:31 2014 : Debug:     max_request_time = 30
Sat Jan 25 23:21:31 2014 : Debug:     cleanup_delay = 5
Sat Jan 25 23:21:31 2014 : Debug:     max_requests = 1024
Sat Jan 25 23:21:31 2014 : Debug:     pidfile = "/var/run/freeradius/freeradius.pid"
Sat Jan 25 23:21:31 2014 : Debug:     checkrad = "/usr/sbin/checkrad"
Sat Jan 25 23:21:31 2014 : Debug:     debug_level = 0
Sat Jan 25 23:21:31 2014 : Debug:     proxy_requests = yes
Sat Jan 25 23:21:31 2014 : Debug:  log {
Sat Jan 25 23:21:31 2014 : Debug:     stripped_names = no
Sat Jan 25 23:21:31 2014 : Debug:     auth = no
Sat Jan 25 23:21:31 2014 : Debug:     auth_badpass = no
Sat Jan 25 23:21:31 2014 : Debug:     auth_goodpass = no
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  security {
Sat Jan 25 23:21:31 2014 : Debug:     max_attributes = 200
Sat Jan 25 23:21:31 2014 : Debug:     reject_delay = 1
Sat Jan 25 23:21:31 2014 : Debug:     status_server = yes
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Loading Realms and Home Servers ####
Sat Jan 25 23:21:31 2014 : Debug:  proxy server {
Sat Jan 25 23:21:31 2014 : Debug:     retry_delay = 5
Sat Jan 25 23:21:31 2014 : Debug:     retry_count = 3
Sat Jan 25 23:21:31 2014 : Debug:     default_fallback = no
Sat Jan 25 23:21:31 2014 : Debug:     dead_time = 120
Sat Jan 25 23:21:31 2014 : Debug:     wake_all_if_all_dead = no
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  home_server localhost {
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 23:21:31 2014 : Debug:     port = 1812
Sat Jan 25 23:21:31 2014 : Debug:     type = "auth"
Sat Jan 25 23:21:31 2014 : Debug:     secret = "testing123"
Sat Jan 25 23:21:31 2014 : Debug:     response_window = 20
Sat Jan 25 23:21:31 2014 : Debug:     max_outstanding = 65536
Sat Jan 25 23:21:31 2014 : Debug:     require_message_authenticator = yes
Sat Jan 25 23:21:31 2014 : Debug:     zombie_period = 40
Sat Jan 25 23:21:31 2014 : Debug:     status_check = "status-server"
Sat Jan 25 23:21:31 2014 : Debug:     ping_interval = 30
Sat Jan 25 23:21:31 2014 : Debug:     check_interval = 30
Sat Jan 25 23:21:31 2014 : Debug:     num_answers_to_alive = 3
Sat Jan 25 23:21:31 2014 : Debug:     num_pings_to_alive = 3
Sat Jan 25 23:21:31 2014 : Debug:     revive_interval = 120
Sat Jan 25 23:21:31 2014 : Debug:     status_check_timeout = 4
Sat Jan 25 23:21:31 2014 : Debug:     irt = 2
Sat Jan 25 23:21:31 2014 : Debug:     mrt = 16
Sat Jan 25 23:21:31 2014 : Debug:     mrc = 5
Sat Jan 25 23:21:31 2014 : Debug:     mrd = 30
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  home_server_pool my_auth_failover {
Sat Jan 25 23:21:31 2014 : Debug:     type = fail-over
Sat Jan 25 23:21:31 2014 : Debug:     home_server = localhost
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  realm example.com {
Sat Jan 25 23:21:31 2014 : Debug:     auth_pool = my_auth_failover
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug:  realm LOCAL {
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Loading Clients ####
Sat Jan 25 23:21:31 2014 : Debug:  client localhost {
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 23:21:31 2014 : Debug:     require_message_authenticator = no
Sat Jan 25 23:21:31 2014 : Debug:     secret = "testing123"
Sat Jan 25 23:21:31 2014 : Debug:     nastype = "other"
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Instantiating modules ####
Sat Jan 25 23:21:31 2014 : Debug:  instantiate {
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_exec, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_exec
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "exec" from file /etc/freeradius/modules/exec
Sat Jan 25 23:21:31 2014 : Debug:   exec {
Sat Jan 25 23:21:31 2014 : Debug:     wait = no
Sat Jan 25 23:21:31 2014 : Debug:     input_pairs = "request"
Sat Jan 25 23:21:31 2014 : Debug:     shell_escape = yes
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_sqlcounter, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_sqlcounter
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "chillispot_max_bytes" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 23:21:31 2014 : Debug:   sqlcounter chillispot_max_bytes {
Sat Jan 25 23:21:31 2014 : Debug:     counter-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 23:21:31 2014 : Debug:     check-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 23:21:31 2014 : Debug:     reply-name = "ChilliSpot-Max-Total-Octets"
Sat Jan 25 23:21:31 2014 : Debug:     key = "User-Name"
Sat Jan 25 23:21:31 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 23:21:31 2014 : Debug:     query = "SELECT SUM(AcctInputOctets) + SUM(AcctOutputOctets) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 23:21:31 2014 : Debug:     reset = "never"
Sat Jan 25 23:21:31 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Reply attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Counter attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Check attribute ChilliSpot-Max-Total-Octets is number 954138627
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Next reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Prev reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "noresetcounter" from file /etc/freeradius/sql/mysql/counter.conf
Sat Jan 25 23:21:31 2014 : Debug:   sqlcounter noresetcounter {
Sat Jan 25 23:21:31 2014 : Debug:     counter-name = "Session-Timeout"
Sat Jan 25 23:21:31 2014 : Debug:     check-name = "Session-Timeout"
Sat Jan 25 23:21:31 2014 : Debug:     reply-name = "Session-Timeout"
Sat Jan 25 23:21:31 2014 : Debug:     key = "User-Name"
Sat Jan 25 23:21:31 2014 : Debug:     sqlmod-inst = "sql"
Sat Jan 25 23:21:31 2014 : Debug:     query = "SELECT SUM(Acctsessiontime) FROM radacct WHERE UserName='%{%k}'"
Sat Jan 25 23:21:31 2014 : Debug:     reset = "never"
Sat Jan 25 23:21:31 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Reply attribute Session-Timeout is number 27
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Counter attribute Session-Timeout is number 27
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Check attribute Session-Timeout is number 27
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Next reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug: rlm_sqlcounter: Current Time: 1390684891 [2014-01-25 23:21:31], Prev reset 0 [2014-01-25 23:00:00]
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_expr, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_expr
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "expr" from file /etc/freeradius/modules/expr
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_expiration, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_expiration
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "expiration" from file /etc/freeradius/modules/expiration
Sat Jan 25 23:21:31 2014 : Debug:   expiration {
Sat Jan 25 23:21:31 2014 : Debug:     reply-message = "Password Has Expired  "
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_logintime, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_logintime
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "logintime" from file /etc/freeradius/modules/logintime
Sat Jan 25 23:21:31 2014 : Debug:   logintime {
Sat Jan 25 23:21:31 2014 : Debug:     reply-message = "You are calling outside your allowed timespan  "
Sat Jan 25 23:21:31 2014 : Debug:     minimum-timeout = 60
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  }
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Loading Virtual Servers ####
Sat Jan 25 23:21:31 2014 : Debug: server inner-tunnel { # from file /etc/freeradius/sites-enabled/inner-tunnel
Sat Jan 25 23:21:31 2014 : Debug:  modules {
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_pap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_pap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "pap" from file /etc/freeradius/modules/pap
Sat Jan 25 23:21:31 2014 : Debug:   pap {
Sat Jan 25 23:21:31 2014 : Debug:     encryption_scheme = "auto"
Sat Jan 25 23:21:31 2014 : Debug:     auto_header = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_chap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_chap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "chap" from file /etc/freeradius/modules/chap
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_mschap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_mschap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "mschap" from file /etc/freeradius/modules/mschap
Sat Jan 25 23:21:31 2014 : Debug:   mschap {
Sat Jan 25 23:21:31 2014 : Debug:     use_mppe = yes
Sat Jan 25 23:21:31 2014 : Debug:     require_encryption = no
Sat Jan 25 23:21:31 2014 : Debug:     require_strong = no
Sat Jan 25 23:21:31 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_unix, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_unix
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "unix" from file /etc/freeradius/modules/unix
Sat Jan 25 23:21:31 2014 : Debug:   unix {
Sat Jan 25 23:21:31 2014 : Debug:     radwtmp = "/var/log/freeradius/radwtmp"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_eap, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_eap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "eap" from file /etc/freeradius/eap.conf
Sat Jan 25 23:21:31 2014 : Debug:   eap {
Sat Jan 25 23:21:31 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 23:21:31 2014 : Debug:     timer_expire = 60
Sat Jan 25 23:21:31 2014 : Debug:     ignore_unknown_eap_types = no
Sat Jan 25 23:21:31 2014 : Debug:     cisco_accounting_username_bug = no
Sat Jan 25 23:21:31 2014 : Debug:     max_sessions = 4096
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_md5
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-md5
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_leap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-leap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_gtc
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-gtc
Sat Jan 25 23:21:31 2014 : Debug:    gtc {
Sat Jan 25 23:21:31 2014 : Debug:     challenge = "Password: "
Sat Jan 25 23:21:31 2014 : Debug:     auth_type = "PAP"
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_tls
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-tls
Sat Jan 25 23:21:31 2014 : Debug:    tls {
Sat Jan 25 23:21:31 2014 : Debug:     rsa_key_exchange = no
Sat Jan 25 23:21:31 2014 : Debug:     dh_key_exchange = yes
Sat Jan 25 23:21:31 2014 : Debug:     rsa_key_length = 512
Sat Jan 25 23:21:31 2014 : Debug:     dh_key_length = 512
Sat Jan 25 23:21:31 2014 : Debug:     verify_depth = 0
Sat Jan 25 23:21:31 2014 : Debug:     CA_path = "/etc/freeradius/certs"
Sat Jan 25 23:21:31 2014 : Debug:     pem_file_type = yes
Sat Jan 25 23:21:31 2014 : Debug:     private_key_file = "/etc/freeradius/certs/server.key"
Sat Jan 25 23:21:31 2014 : Debug:     certificate_file = "/etc/freeradius/certs/server.pem"
Sat Jan 25 23:21:31 2014 : Debug:     CA_file = "/etc/freeradius/certs/ca.pem"
Sat Jan 25 23:21:31 2014 : Debug:     private_key_password = "whatever"
Sat Jan 25 23:21:31 2014 : Debug:     dh_file = "/etc/freeradius/certs/dh"
Sat Jan 25 23:21:31 2014 : Debug:     random_file = "/dev/urandom"
Sat Jan 25 23:21:31 2014 : Debug:     fragment_size = 1024
Sat Jan 25 23:21:31 2014 : Debug:     include_length = yes
Sat Jan 25 23:21:31 2014 : Debug:     check_crl = no
Sat Jan 25 23:21:31 2014 : Debug:     cipher_list = "DEFAULT"
Sat Jan 25 23:21:31 2014 : Debug:     make_cert_command = "/etc/freeradius/certs/bootstrap"
Sat Jan 25 23:21:31 2014 : Debug:     cache {
Sat Jan 25 23:21:31 2014 : Debug:     enable = no
Sat Jan 25 23:21:31 2014 : Debug:     lifetime = 24
Sat Jan 25 23:21:31 2014 : Debug:     max_entries = 255
Sat Jan 25 23:21:31 2014 : Debug:     }
Sat Jan 25 23:21:31 2014 : Debug:     verify {
Sat Jan 25 23:21:31 2014 : Debug:     }
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_ttls
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-ttls
Sat Jan 25 23:21:31 2014 : Debug:    ttls {
Sat Jan 25 23:21:31 2014 : Debug:     default_eap_type = "md5"
Sat Jan 25 23:21:31 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 23:21:31 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 23:21:31 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 23:21:31 2014 : Debug:     include_length = yes
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_peap
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-peap
Sat Jan 25 23:21:31 2014 : Debug:    peap {
Sat Jan 25 23:21:31 2014 : Debug:     default_eap_type = "mschapv2"
Sat Jan 25 23:21:31 2014 : Debug:     copy_request_to_tunnel = no
Sat Jan 25 23:21:31 2014 : Debug:     use_tunneled_reply = no
Sat Jan 25 23:21:31 2014 : Debug:     proxy_tunneled_request_as_eap = yes
Sat Jan 25 23:21:31 2014 : Debug:     virtual_server = "inner-tunnel"
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to sub-module rlm_eap_mschapv2
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating eap-mschapv2
Sat Jan 25 23:21:31 2014 : Debug:    mschapv2 {
Sat Jan 25 23:21:31 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 23:21:31 2014 : Debug:    }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_realm, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_realm
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "suffix" from file /etc/freeradius/modules/realm
Sat Jan 25 23:21:31 2014 : Debug:   realm suffix {
Sat Jan 25 23:21:31 2014 : Debug:     format = "suffix"
Sat Jan 25 23:21:31 2014 : Debug:     delimiter = "@"
Sat Jan 25 23:21:31 2014 : Debug:     ignore_default = no
Sat Jan 25 23:21:31 2014 : Debug:     ignore_null = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_files, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_files
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "files" from file /etc/freeradius/modules/files
Sat Jan 25 23:21:31 2014 : Debug:   files {
Sat Jan 25 23:21:31 2014 : Debug:     usersfile = "/etc/freeradius/users"
Sat Jan 25 23:21:31 2014 : Debug:     acctusersfile = "/etc/freeradius/acct_users"
Sat Jan 25 23:21:31 2014 : Debug:     preproxy_usersfile = "/etc/freeradius/preproxy_users"
Sat Jan 25 23:21:31 2014 : Debug:     compat = "no"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_radutmp, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_radutmp
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "radutmp" from file /etc/freeradius/modules/radutmp
Sat Jan 25 23:21:31 2014 : Debug:   radutmp {
Sat Jan 25 23:21:31 2014 : Debug:     filename = "/var/log/freeradius/radutmp"
Sat Jan 25 23:21:31 2014 : Debug:     username = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:     case_sensitive = yes
Sat Jan 25 23:21:31 2014 : Debug:     check_with_nas = yes
Sat Jan 25 23:21:31 2014 : Debug:     perm = 384
Sat Jan 25 23:21:31 2014 : Debug:     callerid = yes
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_attr_filter, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_attr_filter
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "attr_filter.access_reject" from file /etc/freeradius/modules/attr_filter
Sat Jan 25 23:21:31 2014 : Debug:   attr_filter attr_filter.access_reject {
Sat Jan 25 23:21:31 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.access_reject"
Sat Jan 25 23:21:31 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  } # modules
Sat Jan 25 23:21:31 2014 : Debug: } # server
Sat Jan 25 23:21:31 2014 : Debug: server { # from file /etc/freeradius/radiusd.conf
Sat Jan 25 23:21:31 2014 : Debug:  modules {
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authenticate {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_digest, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_digest
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking authorize {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_preprocess
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Sat Jan 25 23:21:31 2014 : Debug:   preprocess {
Sat Jan 25 23:21:31 2014 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Sat Jan 25 23:21:31 2014 : Debug:     hints = "/etc/freeradius/hints"
Sat Jan 25 23:21:31 2014 : Debug:     with_ascend_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     ascend_channels_per_line = 23
Sat Jan 25 23:21:31 2014 : Debug:     with_ntdomain_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     with_specialix_jetstream_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     with_cisco_vsa_hack = no
Sat Jan 25 23:21:31 2014 : Debug:     with_alvarion_vsa_hack = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_sql, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_sql
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "sql" from file /etc/freeradius/sql.conf
Sat Jan 25 23:21:31 2014 : Debug:   sql {
Sat Jan 25 23:21:31 2014 : Debug:     driver = "rlm_sql_mysql"
Sat Jan 25 23:21:31 2014 : Debug:     server = "localhost"
Sat Jan 25 23:21:31 2014 : Debug:     port = ""
Sat Jan 25 23:21:31 2014 : Debug:     login = "radius"
Sat Jan 25 23:21:31 2014 : Debug:     password = "radpass"
Sat Jan 25 23:21:31 2014 : Debug:     radius_db = "radius"
Sat Jan 25 23:21:31 2014 : Debug:     read_groups = yes
Sat Jan 25 23:21:31 2014 : Debug:     sqltrace = no
Sat Jan 25 23:21:31 2014 : Debug:     sqltracefile = "/var/log/freeradius/sqltrace.sql"
Sat Jan 25 23:21:31 2014 : Debug:     readclients = no
Sat Jan 25 23:21:31 2014 : Debug:     deletestalesessions = yes
Sat Jan 25 23:21:31 2014 : Debug:     num_sql_socks = 5
Sat Jan 25 23:21:31 2014 : Debug:     lifetime = 0
Sat Jan 25 23:21:31 2014 : Debug:     max_queries = 0
Sat Jan 25 23:21:31 2014 : Debug:     sql_user_name = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:     default_user_profile = ""
Sat Jan 25 23:21:31 2014 : Debug:     nas_query = "SELECT id, nasname, shortname, type, secret, server FROM nas"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_check_query = "SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_reply_query = "SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_group_check_query = "SELECT id, groupname, attribute,           Value, op           FROM radgroupcheck           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     authorize_group_reply_query = "SELECT id, groupname, attribute,           value, op           FROM radgroupreply           WHERE groupname = '%{Sql-Group}'           ORDER BY id"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_onoff_query = "          UPDATE radacct           SET              acctstoptime       =  '%S',              acctsessiontime    =  unix_timestamp('%S') -                                    unix_timestamp(acctstarttime),              acctterminatecause =  '%{Acct-Terminate-Cause}',              acctstopdelay      =  %{%{Acct-Delay-Time}:-0}           WHERE acctstoptime IS NULL           AND nasipaddress      =  '%{NAS-IP-Address}'           AND acctstarttime     <= '%S'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_update_query = "           UPDATE radacct           SET              framedipaddress = '%{Framed-IP-Address}',              acctsessiontime     = '%{Acct-Session-Time}',              acctinputoctets     = '%{%{Acct-Input-Gigawords}:-0}'  << 32 |                                    '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets    = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                    '%{%{Acct-Output-Octets}:-0}'           WHERE acctsessionid = '%{Acct-Session-Id}'           AND username        = '%{SQL-User-Name}'           AND nasipaddress    = '%{NAS-IP-Address}'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_update_query_alt = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,      username,              realm,            nasipaddress,      nasportid,              nasporttype,      acctstarttime,     acctsessiontime,              acctauthentic,    connectinfo_start, acctinputoctets,              acctoutputoctets, calledstationid,   callingstationid,              servicetype,      framedprotocol,    framedipaddress,              acctstartdelay,   xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                       INTERVAL (%{%{Acct-Session-Time}:-0} +                                 %{%{Acct-Delay-Time}:-0}) SECOND),                       '%{Acct-Session-Time}',              '%{Acct-Authentic}', '',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Service-Type}', '%{Framed-Protocol}',              '%{Framed-IP-Address}',              '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_start_query = "           INSERT INTO radacct             (acctsessionid,    acctuniqueid,     username,              realm,            nasipaddress,     nasportid,              nasporttype,      acctstarttime,    acctstoptime,              acctsessiontime,  acctauthentic,    connectinfo_start,              connectinfo_stop, acctinputoctets,  acctoutputoctets,              calledstationid,  callingstationid, acctterminatecause,              servicetype,      framedprotocol,   framedipaddress,              acctstartdelay,   acctstopdelay,    xascendsessionsvrkey)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}', '%S', NULL,              '0', '%{Acct-Authentic}', '%{Connect-Info}',              '', '0', '0',              '%{Called-Station-Id}', '%{Calling-Station-Id}', '',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '%{%{Acct-Delay-Time}:-0}', '0', '%{X-Ascend-Session-Svr-Key}')"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_start_query_alt = "           UPDATE radacct SET              acctstarttime     = '%S',              acctstartdelay    = '%{%{Acct-Delay-Time}:-0}',              connectinfo_start = '%{Connect-Info}'           WHERE acctsessionid  = '%{Acct-Session-Id}'           AND username         = '%{SQL-User-Name}'           AND nasipaddress     = '%{NAS-IP-Address}'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_stop_query = "           UPDATE radacct SET              acctstoptime       = '%S',              acctsessiontime    = '%{Acct-Session-Time}',              acctinputoctets    = '%{%{Acct-Input-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Input-Octets}:-0}',              acctoutputoctets   = '%{%{Acct-Output-Gigawords}:-0}' << 32 |                                   '%{%{Acct-Output-Octets}:-0}',              acctterminatecause = '%{Acct-Terminate-Cause}',              acctstopdelay      = '%{%{Acct-Delay-Time}:-0}',              connectinfo_stop   = '%{Connect-Info}'           WHERE acctsessionid   = '%{Acct-Session-Id}'           AND username          = '%{SQL-User-Name}'           AND nasipaddress      = '%{NAS-IP-Address}'"
Sat Jan 25 23:21:31 2014 : Debug:     accounting_stop_query_alt = "           INSERT INTO radacct             (acctsessionid, acctuniqueid, username,              realm, nasipaddress, nasportid,              nasporttype, acctstarttime, acctstoptime,              acctsessiontime, acctauthentic, connectinfo_start,              connectinfo_stop, acctinputoctets, acctoutputoctets,              calledstationid, callingstationid, acctterminatecause,              servicetype, framedprotocol, framedipaddress,              acctstartdelay, acctstopdelay)           VALUES             ('%{Acct-Session-Id}', '%{Acct-Unique-Session-Id}',              '%{SQL-User-Name}',              '%{Realm}', '%{NAS-IP-Address}', '%{NAS-Port}',              '%{NAS-Port-Type}',              DATE_SUB('%S',                  INTERVAL (%{%{Acct-Session-Time}:-0} +                  %{%{Acct-Delay-Time}:-0}) SECOND),              '%S', '%{Acct-Session-Time}', '%{Acct-Authentic}', '',              '%{Connect-Info}',              '%{%{Acct-Input-Gigawords}:-0}' << 32 |              '%{%{Acct-Input-Octets}:-0}',              '%{%{Acct-Output-Gigawords}:-0}' << 32 |              '%{%{Acct-Output-Octets}:-0}',              '%{Called-Station-Id}', '%{Calling-Station-Id}',              '%{Acct-Terminate-Cause}',              '%{Service-Type}', '%{Framed-Protocol}', '%{Framed-IP-Address}',              '0', '%{%{Acct-Delay-Time}:-0}')"
Sat Jan 25 23:21:31 2014 : Debug:     group_membership_query = "SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority"
Sat Jan 25 23:21:31 2014 : Debug:     connect_failure_retry_delay = 60
Sat Jan 25 23:21:31 2014 : Debug:     simul_count_query = ""
Sat Jan 25 23:21:31 2014 : Debug:     simul_verify_query = "SELECT radacctid, acctsessionid, username,                                nasipaddress, nasportid, framedipaddress,                                callingstationid, framedprotocol                                FROM radacct                                WHERE username = '%{SQL-User-Name}'                                AND acctstoptime IS NULL"
Sat Jan 25 23:21:31 2014 : Debug:     postauth_query = "INSERT INTO radpostauth                           (username, pass, reply, authdate)                           VALUES (                           '%{User-Name}',                           '%{%{User-Password}:-%{Chap-Password}}',                           '%{reply:Packet-Type}', '%S')"
Sat Jan 25 23:21:31 2014 : Debug:     safe-characters = "@abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.-_: /"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 0
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #0
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 1
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #1
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 2
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #2
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 3
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #3
Sat Jan 25 23:21:31 2014 : Debug: rlm_sql (sql): starting 4
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sat Jan 25 23:21:31 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sat Jan 25 23:21:31 2014 : Info: rlm_sql (sql): Connected new DB handle, #4
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking preacct {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_acct_unique, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_acct_unique
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "acct_unique" from file /etc/freeradius/modules/acct_unique
Sat Jan 25 23:21:31 2014 : Debug:   acct_unique {
Sat Jan 25 23:21:31 2014 : Debug:     key = "User-Name, Acct-Session-Id, NAS-IP-Address, Client-IP-Address, NAS-Port"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking accounting {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:     (Loaded rlm_detail, checking if it's valid)
Sat Jan 25 23:21:31 2014 : Debug:  Module: Linked to module rlm_detail
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "detail" from file /etc/freeradius/modules/detail
Sat Jan 25 23:21:31 2014 : Debug:   detail {
Sat Jan 25 23:21:31 2014 : Debug:     detailfile = "/var/log/freeradius/radacct/%{Client-IP-Address}/detail-%Y%m%d"
Sat Jan 25 23:21:31 2014 : Debug:     header = "%t"
Sat Jan 25 23:21:31 2014 : Debug:     detailperm = 384
Sat Jan 25 23:21:31 2014 : Debug:     dirperm = 493
Sat Jan 25 23:21:31 2014 : Debug:     locking = no
Sat Jan 25 23:21:31 2014 : Debug:     log_packet_header = no
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Instantiating module "attr_filter.accounting_response" from file /etc/freeradius/modules/attr_filter
Sat Jan 25 23:21:31 2014 : Debug:   attr_filter attr_filter.accounting_response {
Sat Jan 25 23:21:31 2014 : Debug:     attrsfile = "/etc/freeradius/attrs.accounting_response"
Sat Jan 25 23:21:31 2014 : Debug:     key = "%{User-Name}"
Sat Jan 25 23:21:31 2014 : Debug:   }
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking session {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-proxy {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  Module: Checking post-auth {...} for more modules to load
Sat Jan 25 23:21:31 2014 : Debug:  } # modules
Sat Jan 25 23:21:31 2014 : Debug: } # server
Sat Jan 25 23:21:31 2014 : Debug: radiusd: #### Opening IP addresses and Ports ####
Sat Jan 25 23:21:31 2014 : Debug: listen {
Sat Jan 25 23:21:31 2014 : Debug:     type = "auth"
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = *
Sat Jan 25 23:21:31 2014 : Debug:     port = 0
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: listen {
Sat Jan 25 23:21:31 2014 : Debug:     type = "acct"
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = *
Sat Jan 25 23:21:31 2014 : Debug:     port = 0
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: listen {
Sat Jan 25 23:21:31 2014 : Debug:     type = "auth"
Sat Jan 25 23:21:31 2014 : Debug:     ipaddr = 127.0.0.1
Sat Jan 25 23:21:31 2014 : Debug:     port = 18120
Sat Jan 25 23:21:31 2014 : Debug: }
Sat Jan 25 23:21:31 2014 : Debug: Listening on authentication address * port 1812
Sat Jan 25 23:21:31 2014 : Debug: Listening on accounting address * port 1813
Sat Jan 25 23:21:31 2014 : Debug: Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Sat Jan 25 23:21:31 2014 : Debug: Listening on proxy address * port 1814
Sat Jan 25 23:21:31 2014 : Info: Ready to process requests.
 
```

I know creating the database 'radius' isn't part of the instructions, but it has helped resolved the 'Couldn't connect socket to MySQL server' related errors. Am i moving in the right direction in trying to solve my problem? If i am, what can i do next? My comprehension of some of the errors in the debug ding report is limited. Thanks for any help!

edit:

When i try to do a client login, the following is the debug output:
```
 rad_recv: Access-Request packet from host 127.0.0.1 port 37771, id=240, length=295
    ChilliSpot-Version = "1.2.9"
    User-Name = "omniWezkHeWq"
    CHAP-Challenge = 0xa0a6392520bd9ecd4fd4696505708445
    CHAP-Password = 0x006bc5fa8b1471ba7619f4b8a94ba3c23d
    Service-Type = Login-User
    Acct-Session-Id = "52e425d800000002"
    Framed-IP-Address = 10.1.0.3
    NAS-Port-Type = Wireless-802.11
    NAS-Port = 2
    NAS-Port-Id = "00000002"
    Calling-Station-Id = "E8-40-F2-DF-AF-34"
    Called-Station-Id = "00-0A-CD-1F-F6-43"
    NAS-IP-Address = 10.1.0.1
    NAS-Identifier = "nas01"
    WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
    WISPr-Location-Name = "My_HotSpot"
    WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
    Message-Authenticator = 0x399c34b3b1166b663bb267455329830f
Sat Jan 25 23:38:33 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:38:33 2014 : Info: +- entering group authorize {...}
Sat Jan 25 23:38:33 2014 : Info: ++[preprocess] returns ok
Sat Jan 25 23:38:33 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Sat Jan 25 23:38:33 2014 : Info: ++[chap] returns ok
Sat Jan 25 23:38:33 2014 : Info: ++[mschap] returns noop
Sat Jan 25 23:38:33 2014 : Info: ++[digest] returns noop
Sat Jan 25 23:38:33 2014 : Info: [suffix] No '@' in User-Name = "omniWezkHeWq", looking up realm NULL
Sat Jan 25 23:38:33 2014 : Info: [suffix] No such realm "NULL"
Sat Jan 25 23:38:33 2014 : Info: ++[suffix] returns noop
Sat Jan 25 23:38:33 2014 : Info: [eap] No EAP-Message, not doing EAP
Sat Jan 25 23:38:33 2014 : Info: ++[eap] returns noop
Sat Jan 25 23:38:33 2014 : Info: [sql]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 23:38:33 2014 : Info: [sql] sql_set_user escaped user --> 'omniWezkHeWq'
Sat Jan 25 23:38:33 2014 : Debug: rlm_sql (sql): Reserving sql socket id: 4
Sat Jan 25 23:38:33 2014 : Info: [sql]     expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'omniWezkHeWq'           ORDER BY id
Sat Jan 25 23:38:33 2014 : Info: [sql]     expand: SELECT groupname           FROM radusergroup           WHERE username = '%{SQL-User-Name}'           ORDER BY priority -> SELECT groupname           FROM radusergroup           WHERE username = 'omniWezkHeWq'           ORDER BY priority
Sat Jan 25 23:38:33 2014 : Debug: rlm_sql (sql): Released sql socket id: 4
Sat Jan 25 23:38:33 2014 : Info: [sql] User omniWezkHeWq not found
Sat Jan 25 23:38:33 2014 : Info: ++[sql] returns notfound
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Sat Jan 25 23:38:33 2014 : Info: ++[chillispot_max_bytes] returns noop
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Entering module authorize code
Sat Jan 25 23:38:33 2014 : Debug: rlm_sqlcounter: Could not find Check item value pair
Sat Jan 25 23:38:33 2014 : Info: ++[noresetcounter] returns noop
Sat Jan 25 23:38:33 2014 : Info: ++[expiration] returns noop
Sat Jan 25 23:38:33 2014 : Info: ++[logintime] returns noop
Sat Jan 25 23:38:33 2014 : Info: [pap] WARNING! No "known good" password found for the user.  Authentication may fail because of this.
Sat Jan 25 23:38:33 2014 : Info: ++[pap] returns noop
Sat Jan 25 23:38:33 2014 : Info: Found Auth-Type = CHAP
Sat Jan 25 23:38:33 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:38:33 2014 : Info: +- entering group CHAP {...}
Sat Jan 25 23:38:33 2014 : Info: [chap] login attempt by "omniWezkHeWq" with CHAP password
Sat Jan 25 23:38:33 2014 : Info: [chap] Cleartext-Password is required for authentication
Sat Jan 25 23:38:33 2014 : Info: ++[chap] returns invalid
Sat Jan 25 23:38:33 2014 : Info: Failed to authenticate the user.
Sat Jan 25 23:38:33 2014 : Info: Using Post-Auth-Type Reject
Sat Jan 25 23:38:33 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Sat Jan 25 23:38:33 2014 : Info: +- entering group REJECT {...}
Sat Jan 25 23:38:33 2014 : Info: [attr_filter.access_reject]     expand: %{User-Name} -> omniWezkHeWq
Sat Jan 25 23:38:33 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Sat Jan 25 23:38:33 2014 : Info: ++[attr_filter.access_reject] returns updated
Sat Jan 25 23:38:33 2014 : Info: Delaying reject of request 0 for 1 seconds
Sat Jan 25 23:38:33 2014 : Debug: Going to the next request
Sat Jan 25 23:38:33 2014 : Debug: Waking up in 0.9 seconds.
Sat Jan 25 23:38:34 2014 : Info: Sending delayed reject for request 0
Sending Access-Reject of id 240 to 127.0.0.1 port 37771
Sat Jan 25 23:38:34 2014 : Debug: Waking up in 4.9 seconds.
Sat Jan 25 23:38:39 2014 : Info: Cleaning up request 0 ID 240 with timestamp +1022
Sat Jan 25 23:38:39 2014 : Info: Ready to process requests.


```

---

### Post by victor22 on 2014-03-08
Hi there, Getting error when trying to log in from client. Here is the log.


Mon Mar 10 11:29:37 2014 : Info: Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 40425, id=20, length=289
        ChilliSpot-Version = "1.2.9"
        User-Name = "vic249"
        CHAP-Challenge = 0x993d34053c5876c75893b43e51e0b7c1
        CHAP-Password = 0x00333f438dc0292982be487adddba4a4df
        Service-Type = Login-User
        Acct-Session-Id = "531ceb4c00000001"
        Framed-IP-Address = 10.1.0.2
        NAS-Port-Type = Wireless-802.11
        NAS-Port = 1
        NAS-Port-Id = "00000001"
        Calling-Station-Id = "08-00-27-4B-A9-DC"
        Called-Station-Id = "08-00-27-34-77-68"
        NAS-IP-Address = 10.1.0.1
        NAS-Identifier = "nas01"
        WISPr-Location-ID = "isocc=,cc=,ac=,network=Coova,"
        WISPr-Location-Name = "My_HotSpot"
        WISPr-Logoff-URL = "http://10.1.0.1:3990/logoff"
        Message-Authenticator = 0xcc81c6b37c9cd5abc2819583104bc355
Mon Mar 10 11:30:46 2014 : Info: # Executing section authorize from file /etc/freeradius/sites-enabled/default
Mon Mar 10 11:30:46 2014 : Info: +- entering group authorize {...}
Mon Mar 10 11:30:46 2014 : Info: ++[preprocess] returns ok
Mon Mar 10 11:30:46 2014 : Info: [chap] Setting 'Auth-Type := CHAP'
Mon Mar 10 11:30:46 2014 : Info: ++[chap] returns ok
Mon Mar 10 11:30:46 2014 : Info: ++[mschap] returns noop
Mon Mar 10 11:30:46 2014 : Info: ++[digest] returns noop
Mon Mar 10 11:30:46 2014 : Info: [suffix] No '@' in User-Name = "vic249", looking up realm NULL
Mon Mar 10 11:30:46 2014 : Info: [suffix] No such realm "NULL"
Mon Mar 10 11:30:46 2014 : Info: ++[suffix] returns noop
Mon Mar 10 11:30:46 2014 : Info: [eap] No EAP-Message, not doing EAP
Mon Mar 10 11:30:46 2014 : Info: ++[eap] returns noop
Mon Mar 10 11:30:46 2014 : Info: [sql]  expand: %{User-Name} -> vic249
Mon Mar 10 11:30:46 2014 : Info: [sql] sql_set_user escaped user --> 'vic249'
Mon Mar 10 11:30:46 2014 : Info: rlm_sql (sql): Trying to (re)connect unconnected handle 4..
Mon Mar 10 11:30:46 2014 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Mon Mar 10 11:30:46 2014 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Mon Mar 10 11:30:46 2014 : Error: rlm_sql_mysql: Couldn't connect socket to MySQL server radius@localhost:radius
Mon Mar 10 11:30:46 2014 : Error: rlm_sql_mysql: Mysql error 'Access denied for user 'radius'@'localhost' (using password: YES)'
Mon Mar 10 11:30:46 2014 : Error: rlm_sql (sql): Failed to connect DB handle #4
Mon Mar 10 11:30:46 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 4..
Mon Mar 10 11:30:46 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 3..
Mon Mar 10 11:30:46 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 2..
Mon Mar 10 11:30:46 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 1..
Mon Mar 10 11:30:46 2014 : Debug: rlm_sql (sql): Ignoring unconnected handle 0..
Mon Mar 10 11:30:46 2014 : Info: rlm_sql (sql): There are no DB handles to use! skipped 5, tried to connect 1
Mon Mar 10 11:30:46 2014 : Info: ++[sql] returns fail
Mon Mar 10 11:30:46 2014 : Info: Using Post-Auth-Type Reject
Mon Mar 10 11:30:46 2014 : Info: # Executing group from file /etc/freeradius/sites-enabled/default
Mon Mar 10 11:30:46 2014 : Info: +- entering group REJECT {...}
Mon Mar 10 11:30:46 2014 : Info: [attr_filter.access_reject]    expand: %{User-Name} -> vic249
Mon Mar 10 11:30:46 2014 : Debug:  attr_filter: Matched entry DEFAULT at line 11
Mon Mar 10 11:30:46 2014 : Info: ++[attr_filter.access_reject] returns updated
Mon Mar 10 11:30:46 2014 : Info: Delaying reject of request 3 for 1 seconds
Mon Mar 10 11:30:46 2014 : Debug: Going to the next request
Mon Mar 10 11:30:46 2014 : Debug: Waking up in 0.9 seconds.
Mon Mar 10 11:30:47 2014 : Info: Sending delayed reject for request 3
Sending Access-Reject of id 20 to 127.0.0.1 port 40425
Mon Mar 10 11:30:47 2014 : Debug: Waking up in 4.9 seconds.
Mon Mar 10 11:30:52 2014 : Info: Cleaning up request 3 ID 20 with timestamp +413
Mon Mar 10 11:30:52 2014 : Info: Ready to process requests.

---

### Post by ODTech on 2014-03-31
Hi.

I got everything working up to creating a user in daloradius. The user is redirected then they can authenticate and browse.

My problem is the accounting information is not picked up by daloradius so i can't monitor which users are online.
On the daloradius discussion pages someone mentioned that the NAS is not sending the information to the radius or freeradius is not set to write the information into the db.

I followed the howto on this thread..

Anyone got some ideas i can try.

Thanks

---

### Post by bluephoenix2 on 2014-07-04
I asked this on a new thread. No need to reply here.

---

### Post by Azam_Imtiaz on 2014-07-19
Hello everyone 
I have a small problem here with authentication I setup everything as it Wrote by Laughmo but in Last coova chilli not authenticating with daloradius user. 
and I also want to ask you that Can I connect clearos mysql database server and radius server to daloradius+coova installed in my ubuntu box. This is very Important for me I working from 2 weeks to install daloradius+coova chilli in clearos but I failed. Now I buy a new system for ubuntu to install daloradius and coovachilli, I also tried mikrotik but clients complaints me that the Facebook is too slow. they don't like mikrotik and now I am in big trouble please help me. :confused:

---

### Post by karson on 2014-07-23
thank you , i followed  you instruction and it 's work perfectly

---

### Post by Mori_Kernel on 2014-09-14
Hi,


Thanks for your instructions.
I have 50 users and I want to give them 250MB every day.
How do I change sqlcounters in sqlcounter.conf?
What should I do?

---

### Post by jamiwent on 2015-05-09
Is this thread dead? I am looking to do this walkthrough, and would love to know if the original poster will answer questions :D

---

### Post by Ark_74 on 2015-05-17
Does anybody has enable JSON so you can have a status page for each user?

I'm really having a hard time trying to make it work. :O

---

### Post by praveen17 on 2015-07-21
Hey ! What if i only want to install daloRADIUS with out chilly spot! I m going to use PPPOE not hotspot and I will create a PPPOE server on mikrotik router and want to authenticate user using daloRADIUS with freeradius. Is just omitting the chilli spot setup is enough or any thing else?

---

### Post by sobhan2 on 2015-09-25
Hey, Thanks for your great manual, I have just followed the instructions and everything is installed perfectly, but can't see any dhcp running on the server and non if the clients are able to get ip address on eth1, can anyone help me please ?

---

### Post by asif8 on 2015-12-30
Hello Guyz,

Thanks for nice tutorial.

I setup lab in my home using vmware workstation.

2 VM machine. 

First machine Ubuntu has 2 nic 1 NAT 2 hostonly.

2nd machine xp 1nic hostonly which successfully able to redirect to captive portal. But unable to open dalo radius webpage. Also unable to open daloradius page with ubuntu (nat) wan IP from my main (base) windows7 machine. Tried so many things in couple of days but unable so resolve. Can someone help? How can i access daloradius page?

---

### Post by royski_it2004 on 2016-03-09
Hi, is this thread still active?  I've seen that the last post was Dec. 2015, yet.

I tried this tutorial but I get an error, when I add the attribute Max-All-Sessions, I get the error "invalid octet string '3600' for attribute name 'Max-All-Session'", so I remove the said attribute, and was able to have a running chillispot login.

Now, I am trying to find how to setup the daloradius wherein, only one login per user at a time is active, therefore, the same user can't use his/her login on another computer/unit to be able to access the internet, until the first login ends.

I've tried the Simultaneous-Use = 1 Check Attribute but it didn't work.

Any suggestions?

Thanks

---

### Post by Bucky Ball on 2016-03-09
> **royski_it2004 said:**
> Hi, is this thread still active?  I've seen that the last post was Dec. 2015, yet.



Not really. The last post was last December and that was looking for support on an old thread, too. Don't like your chances 70 posts deep on an old thread about 12.04.

Suggest you post a new thread with a descriptive title outlining your issue and link to this one if you need to. Good luck. 

*Thread closed.*

---

