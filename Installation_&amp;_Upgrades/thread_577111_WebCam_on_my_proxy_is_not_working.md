---
title: "WebCam on my proxy is not working"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by Loey on 2007-10-15
hi,
I  have proxy server for small network. Browsing works fine but webcam & voice chat in yahoo messenger is not working also chikka IM. Any idea how to make this things work....? This in my configuration:

> http_port 127.0.0.1:3128
http_port 192.168.88.1:3128
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
access_log /var/log/squid/access.log squid
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl RTP_ports port 5000-5199    # RTP
acl RTP_ports port 6301         # RTP-chikka
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl our_networks src 192.168.1.250 192.168.88.0/24
http_access allow our_networks
http_access allow localhost
http_access deny all
http_reply_access allow !RTP_ports
http_reply_access allow all
icp_access allow all
 cache_mgr [email]linux@example.com[/email] 
cache_effective_group proxy
 visible_hostname sq1.example.com 
httpd_accel_no_pmtu_disc on
httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
coredump_dir /var/spool/squid

---

