---
title: "Installing bind9"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by mick463 on 2012-08-24
Hi i do not know if i am in the correct place so i am sorry if i am . 

I have installed bind 9 which was simple enough. But i have set up Apache2 so i can run 3 websites mick.com.au, jakki.com.au, teagan.com.au all is working well on that end. I would like to set up my own dns but i only have one external ip i have seen this documentation

 [https://help.ubuntu.com/12.04/serverguide/dns-configuration.html#dns-primarymaster-configuration](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html#dns-primarymaster-configuration)

to create a master for mick.com.au how do i point to jakki and teagan and not have mick come up.

Thankyou Mick463.

---

### Post by SeijiSensei on 2012-08-25
If you have one IP address, point the A records for all three hostnames to that address.  Then set up separate <VirtualHost> containers in apache for each site with the [ServerName]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") parameter set accordingly.  

I'll just remind you that [Internet standards]("http://tools.ietf.org/html/rfc1912") require that you maintain both a primary and secondary DNS server.  Just one DNS server does not conform to standards.

---

### Post by mick463 on 2012-08-26
Hi there i have already set up virtual hosts in apache and i will set up another dns as i am suposed to .

I am suposed to copy and edit the /etc/bind/db.local by using the command 
sudo cp /etc/bind/db.local /etc/bind/db.websitename.com which is my A record for each of my web pages.
 
but the ubuntu page says i am suposed to also first edit the /etc/bind/named.conf.local: like so 

zone "example.com" {
	type master;
        file "/etc/bind/db.example.com";
};

my question is if i edit the /etc/bind/named.conf.local: with say mick.com how is the dns suposed to know where my other A records are (jakki.com and teagan.com as example.com is suposed to have mick.com.

Am i suposed to have 3 entries for each of my websites in the /etc/bind/named.conf.local: like so 

zone "mick.com" {
	type master;
        file "/etc/bind/db.mick.com";
};

zone "jakki.com" {
	type master;
        file "/etc/bind/db.jakki.com";
};

zone "teagan.com" {
	type master;
        file "/etc/bind/db.teagan.com";
};

or is jakki and teagan suposed to be in another file somewhere else.
Regards Mick463.

---

### Post by SeijiSensei on 2012-08-26
> Am i suposed to have 3 entries for each of my websites in the /etc/bind/named.conf.local: like so

Yes, you need a separate entry in named.conf for each zone, and a corresponding zone file with the actual records.

---

### Post by mick463 on 2012-08-26
Thank you very much mate i will put that into action tomorrow and let you know how i go.

Cheers Mick463.

---

### Post by mick463 on 2012-08-26
It seems to have worked thank you for your help.

Cheers Mick463.

---

