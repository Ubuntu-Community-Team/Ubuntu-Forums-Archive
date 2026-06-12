---
title: "install ubuntu10.10 from customer mirror"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by richard_wu0313 on 2011-04-13
hi all,
i want to install ubuntu10.10 from customer mirror. such as i copied ubuntu10.10 alternative image to some folder in server 10.1.1.2 and then used pxe to install os. when selecting mirror, i inputted "http://10.1.1.2/ubuntu/ubuntu10.10/x64". but i couldn't download file to install automatically, and got following error message in red. however, i inputted "wget http://10.1.1.2/ubuntu/ubuntu10.10/x64/fileA", i could download the fileA. any suggestion?


[COLOR="Red"]wget: server returned error:HTTP/1.1 404 not found
wget: bad address 'security.ubuntu.com'[/COLOR]

---

### Post by richard_wu0313 on 2011-04-19
after i set following cfg, previous error disappear, but new error happen.

# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string xx.xx.xx.xx
d-i apt-setup/security_path string /ubuntu


new error:
[COLOR="Red"]wget: server returned error:HTTP/1.1 404 not found
wget: bad address ''
warning **:package retrieval failed[/COLOR]

---

