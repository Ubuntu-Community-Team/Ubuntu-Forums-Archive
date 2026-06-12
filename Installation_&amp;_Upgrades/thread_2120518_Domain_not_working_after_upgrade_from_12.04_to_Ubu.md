---
title: "Domain not working after upgrade from 12.04 to Ubuntu 12.10"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by zenbuddha77 on 2013-02-26
[SIZE=2][COLOR=#FF0000][COLOR=Black]After attempting [SIZE=2]a failed upgrade from the command line I had to reinstall Ubuntu 12.10 completely with an iso image dis[SIZE=2]c. Have not yet [SIZE=2]gone[/SIZE] through the process of reinstalling from my back-up because if this problem is not resolved I am going back to Ubuntu 12.04.

[SIZE=2]Below [SIZE=2]is all the data I have entered using the Ubuntu Guide to reset my broomeunderground.com domain on my private server. Yet de[SIZE=2]spite [SIZE=2]tests showing that things are working I get unable to connect to broomeunderground.com or using my IP address. Any ideas, guys, where I am going wr[SIZE=2]ong? All suggestions would be greatly appreciated.[/SIZE][/SIZE] [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE]
[B]
[COLOR=Red]The f[/COLOR][/B][COLOR=#FF0000]**our directories [SIZE=2]I[/SIZE] edited with nano: **[/COLOR]
1. /etc/bind/named.conf.options
2. /etc/bind/[db.broomeunderground.com]("http://db.broomeunderground.com") 
3. /etc/bind/db.192 
 4. /etc/bind/named.conf.local

And created the two DataBases
1. [db.broomeunderground.com]("http://db.broomeunderground.com")
2. db.192

[COLOR=#33CC00]
[B][COLOR=#000000]1.)[/COLOR] nano /etc/bind/named.conf.options

[/B][/COLOR]
[COLOR=#3333FF][B]         forwarders {
                        [COLOR=#FF0000]209.18.47.61[/COLOR];
                    };

[/B][/COLOR][B]2a) Create DataBase: sudo cp /etc/bind/db.local /etc/bind/[COLOR=#FF0000][db.broomeunderground.com]("http://db.broomeunderground.com")[/COLOR]
[COLOR=#33CC00]   [COLOR=#000000]2b)[/COLOR] nano /etc/bind/[db.broomeunderground.com]("http://db.broomeunderground.com")[/COLOR][/B]

[COLOR=#3333FF][B]
;
; BIND data file for [COLOR=#FF0000][broomeunderground.com]("http://broomeunderground.com")[/COLOR]
;
$TTL 604800
  @      IN     SOA     [COLOR=#FF0000][broomeunderground.com]("http://broomeunderground.com").[/COLOR]          [COLOR=#FF0000][admin.broomeunderground.com]("http://admin.broomeunderground.com").[/COLOR] (
                         [2013022201]("tel:2013022201")                 ; Serial
                      604800                     ; Refresh
                      86400                      ; Retry
                        2419200                    ; Expire
                      604800)                    ; Negative Cache TTL
       IN     A       74.67.98.211
;
@      IN     NS      [COLOR=#FF0000][ns.broomeunderground.com]("http://ns1.broomeunderground.com").[/COLOR]
   @      IN     A       74.67.98.211
@      IN     AAAA    ::1
ns     IN     A       74.67.98.211[/B][/COLOR]


[B]3a) Create DataBase: sudo cp /etc/bind/db.127 /etc/bind/[COLOR=#FF0000]db.192[/COLOR][COLOR=#FF0000]
   [/COLOR][/B]**3b)  [COLOR=#33CC00]nano /e[/COLOR]**[COLOR=#33CC00]**tc/bind/db.192**[/COLOR]

[B];
; BIND reverse data file for 74.67.98.211 com
 ;
$TTL    604800
@       IN      SOA     [COLOR=#FF0000][ns.broomeunderground.com]("http://ns.broomeunderground.com").[/COLOR]   [COLOR=#FF0000][admin.broomeunderground.com]("http://admin.broomeunderground.com").[/COLOR] (
                            [2013022201]("tel:2013022201")     ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                          2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
10      IN      PTR     [COLOR=#FF0000][ns.broomeunderground.com]("http://ns.broomeunderground.com").[/COLOR][/B]

**4. [COLOR=#33CC00]nano /etc/bind/named.conf.local[/COLOR]**


[COLOR=#3333FF][B]//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
   include "/etc/bind/zones.rfc1918";
   
zone  "[COLOR=#FF0000][broomeunderground.com]("http://broomeunderground.com")[/COLOR]" {
          type master;
          file "/etc/bind/[COLOR=#FF0000][db.broomeunderground.com]("http://db.broomeunderground.com")[/COLOR]";
   };

zone  "[COLOR=#FF0000]98.67.74[/COLOR].in-addr.arpa" {
          type master;
          file "/etc/bind/[COLOR=#FF0000]db.192[/COLOR]";
};
    [/B][/COLOR][B]
However I do get this error when using restart for apache2 though using apache2 reload appears to be OK:[/B]

root@serv1ubuntu1210:/home/tom# sudo service apache2 restart
Syntax error on line 1 of /etc/apache2/sites-enabled/nano.save:
Invalid command 'VirtualHost', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
root@serv1ubuntu1210:/home/tom# sudo service apache2 reload
 * Reloading web server config                                           [ OK ] 
root@serv1ubuntu1210:/home/tom# 

**In file nano.save:**

VirtualHost *:80>
       ServerAdmin webmaster@localhost

       Document Root /var/www/broomeunderground.com
       ServerName  broomeunderground.com


**TESTING**

root@serv1ubuntu1210:/home/tom# dig -x 74.67.98.211

; <<>> DiG 9.8.1-P1 <<>> -x 74.67.98.211
;; global options: +cmd
  ;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60668
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;211.98.67.74.in-addr.arpa.    IN    PTR

   ;; ANSWER SECTION:
211.98.67.74.in-addr.arpa. 43200 IN    PTR    [cpe-74-67-98-211.stny.res.rr.com]("http://cpe-74-67-98-211.stny.res.rr.com").

;; Query time: 27 msec
;; SERVER: 209.18.47.61#53(209.18.47.61)
   ;; WHEN: Mon Feb 25 17:13:01 2013
;; MSG SIZE  rcvd: 89

root@serv1ubuntu1210:/home/tom# 

**To test our example Forward zone file enter the following from a command prompt:**

root@serv1ubuntu1210:/home/tom# named-checkzone [broomeunderground.com]("http://broomeunderground.com") /etc/bind/[db.broomeunderground.com]("http://db.broomeunderground.com")
   
zone [broomeunderground.com/IN]("http://broomeunderground.com/IN"): loaded serial [2013022201]("tel:2013022201")
OK
root@serv1ubuntu1210:/home/tom#
  
**Similarly, to test the Reverse zone file enter the following:**

root@serv1ubuntu1210:/home/tom#  named-checkzone 98.67.74.in-addr.arpa /etc/bind/db.192
zone 98.67.74.in-addr.arpa/IN: loaded serial [2013022201]("tel:2013022201")
  OK
root@serv1ubuntu1210:/home/tom#

---

### Post by zenbuddha77 on 2013-02-27
:p FOR AN ASIDE: Originally I was very unhappy with how Ubuntu 12.10 was working with Gnome desktop. Pages were painfully slow at loading and the cursor was virtually impossible to use. I learned yesterday that this had a lot to do with 12.10 not supporting [**Unity 2D**]("http://www.omgubuntu.co.uk/2012/08/unity-2d-removed-from-ubuntu-12-10") and followed a suggestion to install and use [**LXDE**]("http://www.youtube.com/watch?v=M3HmcqQtjKg") desktop with 12.10. The difference in page loading speed and cursor use has been AMAZING!

Apparently Unity 2D was designed to work with older slower computer/servers while now there is Unity 3D which has something to do with *LLVMpipe *which IS installed on my server that has 4 processors and is only about 9  mos old*. *So I am more than a little surprised that my hardware wasn't able to handle the power use of Ubuntu 12.10 using Gnome desktop. Still working on this DNS problem but as soon as I get that resolved going to see if I can tweak 12.10 a bit to have 3D/LLVMpipe work and/or configured properly.

---

