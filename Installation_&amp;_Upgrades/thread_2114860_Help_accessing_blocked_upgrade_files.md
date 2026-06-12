---
title: "Help accessing blocked upgrade files"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by dckirba on 2013-02-11
Hello all,

How are you doing?

I have a small request for help. The country where I reside has a blanket block on anything that says "proxy". I was running updates on my laptop (12.04.1 i386) and four files were not downloadable because they have "proxy" in their names. I would really appreciate it if someone would download the files for me, rename them so there is no proxy in the name, and share them somewhere I can download them.

The links to the files are:

[LIST=1]
[*][http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/libproxy1-plugin-networkmanager_0.4.7-0ubuntu4.1_i386.deb]("http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/libproxy1-plugin-networkmanager_0.4.7-0ubuntu4.1_i386.deb")
[*][http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/libproxy1-plugin-gsettings_0.4.7-0ubuntu4.1_i386.deb]("http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/libproxy1-plugin-gsettings_0.4.7-0ubuntu4.1_i386.deb")
[*][http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/libproxy1_0.4.7-0ubuntu4.1_i386.deb]("http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/libproxy1_0.4.7-0ubuntu4.1_i386.deb")
[*][http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/python-libproxy_0.4.7-0ubuntu4.1_all.deb]("http://ftp.heanet.ie/pub/ubuntu/pool/main/libp/libproxy/python-libproxy_0.4.7-0ubuntu4.1_all.deb")
[/LIST]

Thank you for your time,

David

---

### Post by dino99 on 2013-02-11
the easiest way is to change your dns into the network config (use 8.8.8.8 and/or 4.4.4.4  which are the google's ones, or opendns, or ...)

[http://www.google.fr/#hl=fr&gs_rn=2&gs_ri=serp&pq=ubuntu%20boot%20time&cp=23&gs_id=4f&xhr=t&q=ubuntu+bypass+forbidden&es_nrs=true&pf=p&tbo=d&sclient=psy-ab&oq=ubuntu+bypass+forbidden&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=1b1ca8af32702f6d&biw=1674&bih=893](http://www.google.fr/#hl=fr&gs_rn=2&gs_ri=serp&pq=ubuntu%20boot%20time&cp=23&gs_id=4f&xhr=t&q=ubuntu+bypass+forbidden&es_nrs=true&pf=p&tbo=d&sclient=psy-ab&oq=ubuntu+bypass+forbidden&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=1b1ca8af32702f6d&biw=1674&bih=893)

[http://www.liberiangeek.net/2012/11/change-the-dns-server-addresses-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/11/change-the-dns-server-addresses-in-ubuntu-12-10-quantal-quetzal/)

---

### Post by dckirba on 2013-02-11
> **dino99 said:**
> the easiest way is to change your dns into the network config (use 8.8.8.8 and/or 4.4.4.4  which are the google's ones, or opendns, or ...)

Hi Dino,

Thank you for your time. I am using Google's DNS servers. I still have the same problem. There are other sites that are also inaccessible whether you use other DNS servers or the ISP's. It's a countrywide block :(

Thanks,
David

---

### Post by dino99 on 2013-02-11
i know what you means ;)

using google's ones might be too easy (also redirected by your isp i suppose).
So you better change for a small dns (not blacklisted by the isp) like 

68.169.47.32
174.37.130.4

[http://hackercodex.com/guide/how-to-stop-isp-dns-server-hijacking/](http://hackercodex.com/guide/how-to-stop-isp-dns-server-hijacking/)

---

### Post by SlugSlug on 2013-02-11
PM you link

---

