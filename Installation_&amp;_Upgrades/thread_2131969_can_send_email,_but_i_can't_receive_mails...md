---
title: "can send email, but i can't receive mails.."
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by arginafi on 2013-04-03
i installed dovecot-postfix, and squirrelmail and i can't receive emails...

---

### Post by SeijiSensei on 2013-04-03
First thing is to ask your provider whether they are blocking inbound traffic on port 25, the SMTP port.  Many ISPs block that port to enforce their "no-servers" rule on residential connections.  You did read your Terms of Service to determine whether you can run servers, right?

---

### Post by darkod on 2013-04-03
And very close to the first thing is: have you configured the domain to send the emails to your mailserver? Simply installing postfix is not enough, for people to send you emails the DNS has to know where to send them.

Are you using the registrars nameservers or your own?

Either way, do you have a host created pointing to your public IP?
Do you have MX record pointed to that host?

Have you purchased a domain at all?

---

### Post by SeijiSensei on 2013-04-03
Oh, and postfix and dovecot are configured by default to listen only on the 127.0.0.1 "localhost" interface.  You need to change the "mynetworks" entry in Postfix's main.cf and the "listen" entry in dovecot.conf to allow them to accept traffic over the network.

---

### Post by arginafi on 2013-04-03
it's ok, my ISP has no rules for that.It worked until today, but i reinstalled ubuntu, and now i can't manage to fix it.

---

### Post by arginafi on 2013-04-03
I can send emails for example to my gmail account, i can connect from a client-side to mail-server, i configured outlook... all ok... just i can't receive any email...

---

### Post by darkod on 2013-04-03
Look above what Sensei said about the postfix listen configuration. And also at DNS. Postfix will always send emails, to receive them properly you need the DNS setup correctly.

Is it possible your public IP changed?

---

### Post by arginafi on 2013-04-03
no, my ip doesen't changed... i think DNS is configured propertly...

---

### Post by arginafi on 2013-04-03
My local ip is 192.168.1.101 , my public ip is 86.106.196.139 , and my domain is bluetree.ro
__
so ... my hostname is ArgiLinux
__
Hosts:  cat /etc/hosts127.0.0.1       localhost.localdomain localhost ArgiLinux
86.106.196.139  ns1.bluetree.ro


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

___



root@ArgiLinux:/etc/bind# cat named.conf.local
//
// Do any local configuration here
//
zone bluetree.ro {
        type master;
        file "/etc/bind/db.bluetree.ro";
};


zone 139.196.106.86.in-addr.arpa {
        type master;
        file "/etc/bind/139.196.106.86.in-addr.arpa";
};


_____
root@ArgiLinux:/etc/bind# cat db.bluetree.ro
;
; BIND zone definition file for bluetree.ro
;
$TTL    604800
bluetree.ro.      IN      SOA      ns1.bluetree.ro. admin.bluetree.ro. (
                        2011072601; Serial
                        28800
                        3600
                        604800
                        38400
)


; Nameserver and mailserver (replace with your own hostnames):
bluetree.ro.        IN     NS           ns1.bluetree.ro.
bluetree.ro.        IN     MX     10    mail.bluetree.ro.


; IP addresses of local hosts (replace the lines with your own hosts):
                IN      A       86.106.196.139
server          IN      A       86.106.196.139
ns1             IN      A       86.106.196.139
mail            IN      A       86.106.196.139
www             IN      CNAME   server


_____


;
; BIND reverse zone file for bluetree.ro
;
$TTL    604800
@ IN SOA ns1.bluetree.ro. admin.bluetree.ro. (
                        2011072601; Serial
                        28800;
                        604800;
                        604800;
                        86400
)


; IP addresses of local hosts (replace the lines with your own hosts):
        IN      NS      ns1.bluetree.ro.
139       IN      PTR     bluetree.ro
139       IN      PTR     mail.bluetree.ro
139       IN      PTR     [www.bluetree.ro](www.bluetree.ro)

__ 

This is my dns configuration..

---

### Post by darkod on 2013-04-03
Did you make sure port 25 on your router is forwarded to 192.168.1.101?

And that postfix can accept mail on 192.168.1.101 too, not only 127.0.0.1?

---

### Post by arginafi on 2013-04-03
yes, router is configured propertly... until today worked... i reinstalled ubuntu today...
Postfix accepts 192.168.1.101 too..

---

### Post by arginafi on 2013-04-03
This is my main.cf

argi@ArgiLinux:~$ cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version




# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = bluetree.ro
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = bluetree.ro, mail.bluetree.ro, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 , 192.168.1.101
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command =
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
inet_protocols = all

---

### Post by darkod on 2013-04-03
I have no clue, sorry. The DNS seems configured properly. Did you activate the firewall on the server maybe? That would block the incoming connections.

Try to remember all the configuration you did the first time, maybe you missed something after reinstalling the server. Maybe it's something you have to do.

---

### Post by darkod on 2013-04-03
In main.cf for 'mynetworks' try 192.168.1.0/24 instead of putting directly 192.168.1.101. Save and close the file, reboot the server.

I don't have more ideas.

---

### Post by arginafi on 2013-04-03
i disabled now firewall... and still don't work:(..

---

### Post by arginafi on 2013-04-03
in resolv.conf i have
search bluetree.ro
nameserver 192.168.1.101 
Should i change nameserver to public ip address?

---

### Post by darkod on 2013-04-03
I think for the server itself it would be better to have public DNS. But that shouldn't be the problem here.

---

### Post by SeijiSensei on 2013-04-05
I ran this test:

```

# host -t mx bluetree.ro
bluetree.ro mail is handled by 10 mail.bluetree.ro.
# host mail.bluetree.ro
mail.bluetree.ro has address 86.106.196.139
# telnet mail.bluetree.ro 25
Trying 86.106.196.139...

```

I don't get any response.  So either (a) your ISP is blocking inbound port 25; (b) you haven't forwarded the port correctly; or (c) Postfix isn't listening on the correct interface.

---

### Post by arginafi on 2013-04-06
# telnet mail.bluetree.ro 25
Trying 86.106.196.139...
Connected to mail.bluetree.ro.
Escape character is '^]'.
220 bluetree.ro ESMTP Postfix (Ubuntu)

But i don't receive mail from local email to local email ....  with mutt or thunderbird. 
The Router is corectly forwarded to SMTP external/internal port 25, protocol TCP and ip of server.

most probably is from Postfix, the ISP is not blocking port 25 for sure.

i read somewhere that an be from hostname...i changed after instalation, can it be ?

---

### Post by arginafi on 2013-04-06
[COLOR=green][FONT=Times New Roman]Success:[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman] I can see your service on [/FONT][/COLOR][B]86.106.196.139 on port ([B]25)
Your ISP is not blocking port 25

checked with a dns checker from internet. [/B][/B]

---

### Post by lisati on 2013-04-06
I can confirm that telnet'ing into your server that there's basic access.

Do your system logs, in particular /var/log/mail.log, provide any clues after you've tried to send mail via Thunderbird or Mutt?

---

### Post by arginafi on 2013-04-06
hmm :) 
Apr  6 11:31:41 localhost postfix/smtpd[30445]: connect from nm10-vm0.bullet.mail.bf1.yahoo.com[98.139.213.147]
Apr  6 11:31:41 localhost postfix/smtpd[30445]: 9E8BE1A1FF5: client=nm10-vm0.bullet.mail.bf1.yahoo.com[98.139.213.147]
Apr  6 11:31:42 localhost postfix/cleanup[30450]: 9E8BE1A1FF5: message-id=<1365237094.32398.YahooMailNeo@web142706.mail.bf1.yahoo.com>
Apr  6 11:31:42 localhost postfix/qmgr[30398]: 9E8BE1A1FF5: from=<argi.nafi@yahoo.com>, size=3476, nrcpt=1 (queue active)
Apr  6 11:31:42 localhost dovecot: lda(argi): msgid=<1365237094.32398.YahooMailNeo@web142706.mail.bf1.yahoo.com>: saved mail to INBOX
Apr  6 11:31:42 localhost postfix/local[30451]: 9E8BE1A1FF5: to=<argi@bluetree.ro>, relay=local, delay=0.89, delays=0.7/0/0/0.18, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}")
Apr  6 11:31:42 localhost postfix/qmgr[30398]: 9E8BE1A1FF5: removed
Apr  6 11:31:42 localhost postfix/smtpd[30445]: disconnect from nm10-vm0.bullet.mail.bf1.yahoo.com[98.139.213.147]



i send a email from yahoo to domain... and this is syslog...

---

### Post by darkod on 2013-04-06
It seems to say it's saved in INBOX. Can you check? Do you have some MDA installed like dovecot?

Otherwise the mail might be sitting in a folder inside your Home folder (depending how you set up postfix) but you might not be aware of it.

---

### Post by arginafi on 2013-04-06
i reinstalled postfix and dovecot, and after that i was receiving emails(the log i posted earlier), and i just set [COLOR=#000000]mail_location = maildir:/home/%u/Maildir, to save mails in right path.

Thank you everyone for help! [/COLOR]

---

