---
title: "Squid3 wont start"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by DUCKFACE on 2012-08-10
hello there
i have a huge problem with this squid3. its second day that im trying to start it. it wint start on bootup and it wont start on 
```
service squid3 start
```actualy on squid3 start i get squid3 start/running, process 13577
but on 
**> ps auxww | fgrep squid3** ```
root     14073  0.0  0.0   4392   604 ?        S    23:46   0:00 sh -c su root -c ps\ auxww\ \|\ fgrep\ squid3 2>&1 root     14074  0.0  0.0  54944  1596 ?        S    23:46   0:00 su root -c ps auxww | fgrep squid3 root     14081  0.0  0.0  12296  1204 ?        S    23:46   0:00 bash -c ps auxww | fgrep squid3 root     14083  0.0  0.0   9300   708 ?        S    23:46   0:00 fgrep squid3
```so no squid3 ps

here is my conf file
```
  #     WELCOME TO SQUID 3.1.19
  #     ----------------------------
   
  acl manager proto cache_object
  acl localhost src 127.0.0.1/32 ::1
  acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
  acl localnet src 10.8.0.1 
   
  # NETWORK OPTIONS
  # -----------------------------------------------------------------------------
   
  #  TAG: http_port
  http_port 10.8.0.1:3128 intercept 
  http_port 127.0.0.1:3128 intercept
   
  # Squid normally listens to port 3128
  http_port 3128 intercept 
   
  #  TAG: hierarchy_stoplist
  hierarchy_stoplist cgi-bin ? 
  #acl QUERY urlpath_regex cgi-bin ?#cache deny QUERYacl apache rep_header Server ^Apache   
  #  TAG: SSL_ports
  acl SSL_ports port 443 # https
  acl SSL_ports port 563 # snews 
  acl SSL_ports port 873 # cups
   
  #  TAG: Safe_ports
  acl Safe_ports port 21       # ftp 
  acl Safe_ports port 22       # ssh
  acl Safe_ports port 70       # gopher 
  acl Safe_ports port 80       # http
  acl Safe_ports port 210      # wais 
  acl Safe_ports port 280      # http-mgmt
  acl Safe_ports port 443      # https
  acl Safe_ports port 488      # gss-http
  acl Safe_ports port 591      # filemaker
  acl Safe_ports port 631      # multiling http
  acl Safe_ports port 777      # multiling http 
  acl Safe_ports port 873      # cups
  acl Safe_ports port 901      # rsync
  acl Safe_ports port 10000    # Webmin 
  acl Safe_ports port 1025-65535     # unregistered ports 
   
  # TAG: method
  acl PURGE method PURGE
  acl CONNECT method CONNECT
   
  http_access allow manager localhost
  http_access deny manager
   
  # Deny requests to certain unsafe ports
  http_access deny !Safe_ports
   
  # Deny CONNECT to other than secure SSL ports
  http_access deny CONNECT !SSL_ports
   
  # TIME OPTIONS
  # -----------------------------------------------------------------------------
  acl officetime time MTWHFA 10:00-17:00
   
  # ADVERTISEMENT OPTIONS
  # -----------------------------------------------------------------------------
   
  acl ads_deny dstdomain "/etc/squid3/ads_deny.acl"acl ads_deny_administrators dstdomain "/etc/squid3/ads_deny_administrators.acl" acl ads_deny_powerusers dstdomain "/etc/squid3/ads_deny_powerusers.acl"acl ads_deny_users dstdomain "/etc/squid3/ads_deny_users.acl"   
  # SITES OPTIONS
  # -----------------------------------------------------------------------------
   
  acl sites_allow dstdomain "/etc/squid3/sites_allow.acl"acl sites_deny dstdomain "/etc/squid3/sites_deny.acl"acl sites_allow_administrators dstdomain "/etc/squid3/sites_allow_administrators.acl"acl sites_deny_administrators dstdomain "/etc/squid3/sites_deny_administrators.acl" acl sites_allow_powerusers dstdomain "/etc/squid3/sites_allow_powerusers.acl"acl sites_deny_powerusers dstdomain "/etc/squid3/sites_deny_powerusers.acl"acl sites_allow_users dstdomain "/etc/squid3/sites_allow_users.acl"acl sites_deny_users dstdomain "/etc/squid3/sites_deny_users.acl"   
  # PROGRAMS OPTIONS
  # -----------------------------------------------------------------------------
   
  acl skype url_regex ^[0-9]+.[0-9]+.[0-9]+.[0-9]+           #skype   # FILES OPTIONS
  # -----------------------------------------------------------------------------#acl files_allow_administrators_up rep_mime_type –i "/etc/squid3/files_allow_administrators.acl"#acl files_deny_administrators_up rep_mime_type -i "/etc/squid3/files_deny_administrators.acl" #acl files_allow_administrators_down req_mime_type -i "/etc/squid3/files_allow_administrators.acl"#acl files_deny_administrators_down req_mime_type -i "/etc/squid3/files_deny_administrators.acl" #acl files_allow_powerusers_up rep_mime_type -i "/etc/squid3/files_allow_powerusers.acl"#acl files_deny_powerusers_up rep_mime_type -i "/etc/squid3/files_deny_powerusers.acl"#acl files_allow_powerusers_down req_mime_type -i "/etc/squid3/files_allow_powerusers.acl"#acl files_deny_powerusers_down req_mime_type -i "/etc/squid3/files_deny_powerusers.acl" #acl files_allow_users_up rep_mime_type -i "/etc/squid3/files_allow_users.acl"#acl files_deny_users_up rep_mime_type -i "/etc/squid3/files_deny_users.acl"#acl files_allow_users_down req_mime_type -i "/etc/squid3/files_allow_users.acl"  #acl files_deny_users_down req_mime_type -i "/etc/squid3/files_deny_users.acl" 
  deny_info err_files_administrators_down files_deny_administrators_down 
  deny_info err_files_powerusers_down files_deny_powerusers_down 
  deny_info err_files_users_down files_deny_users_down   # USERS OPTIONS
  # -----------------------------------------------------------------------------
   
  acl users src 10.8.0.21-10.8.0.25
  acl powerusers src 10.8.0.11
  acl adminsitrators src 10.8.0.2
   
  # ALLOW DENY
  # -----------------------------------------------------------------------------
   
  http_access allow localhost
   
  #allowed sites 
  http_access allow sites_allow 
   
  #denyed sites 
  http_access deny sites_deny
   
  #Adminsitrators options 
  http_access allow adminsitrators sites_allow_administrators 
  #http_access allow adminsitrators files_allow_administrators_up 
  #http_access allow adminsitrators files_allow_administrators_down 
  http_access deny  adminsitrators sites_deny_administrators 
  http_access deny  adminsitrators ads_deny_administrators 
  #http_access deny       adminsitrators files_deny_administrators_up 
  #http_access deny       adminsitrators files_deny_administrators_down 
  http_access allow adminsitrators 
   
  #Powerusers options 
  http_access allow powerusers sites_allow_powerusers 
  #http_access allow powerusers files_allow_powerusers_up  
  #http_access allow powerusers files_allow_powerusers_down 
  http_access deny  powerusers sites_deny_powerusers 
  http_access deny  powerusers ads_deny_powerusers 
  #http_access deny       powerusers files_deny_powerusers_up  
  #http_access deny       powerusers files_deny_powerusers_down 
  http_access allow powerusers 
   
  #Users options 
  http_access allow users sites_allow_users 
  #http_access allow users files_allow_users_up  
  #http_access allow users files_allow_users_down 
  http_access deny  users sites_deny_users  
  http_access deny  users ads_deny_users 
  #http_access deny users files_deny_users_up  
  #http_access deny users files_deny_users_down 
  http_access deny  users CONNECT skype 
  http_access allow users
   
  # And finally deny all other access to this proxy
  http_access deny all
   
  # MEMORY CACHE OPTIONS
  # -----------------------------------------------------------------------------
   
  #  TAG: cache_mem (bytes)
  cache_mem 256 MB
  maximum_object_size 100 MBminimum_object_size 1 KB   
  #  TAG: maximum_object_size_in_memory    (bytes)
  maximum_object_size_in_memory 512 KB
   
  #  TAG: cache_dir
  cache_dir ufs /var/spool/squid3 7000 16 256
   
  #  TAG: access_log
  access_log /var/log/squid3/access.log squid
   
  #  TAG: cache_store_log
  cache_store_log /var/log/squid3/store.log
   
  #  TAG: logfile_rotate
  logfile_rotate 10
   
  # OPTIONS FOR TROUBLESHOOTING
  # -----------------------------------------------------------------------------
   
  #  TAG: cache_log
  cache_log /var/log/squid3/cache.log
   
  #  TAG: coredump_dir
  coredump_dir /var/spool/squid3
   
  # OPTIONS FOR TUNING THE CACHE
  # -----------------------------------------------------------------------------
   
  #  TAG: refresh_pattern
  refresh_pattern ^ftp:        1440  20%   10080
  refresh_pattern ^gopher:     1440  0%    1440
  refresh_pattern -i (/cgi-bin/|\?) 0 0%    0
  refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
  # example lin deb packages
  refresh_pattern .             0     20%   4320
  refresh_pattern -i .(gif|png|jpg|jpeg|ico)$ 4320000 90% 4320000 override-expire ignore-no-cache ignore-no-store ignore-privaterefresh_pattern -i .(iso|avi|wva|mpg|wav|mp3|mp4|mpeg|swf|flv|x-flv|pdf)$ 4320000 90% 4320000 override-expire ignore-no-cache ignore-no-store ignore-privaterefresh_pattern -i .(deb|udeb|rpm|exe|zip|tar|tgz|ram|rar|bin|ppt|doc|tiff)$ 4320000 90% 4320000 override-expire ignore-no-cache ignore-no-store ignore-privaterefresh_pattern -i .index.(html|htm)$ 0 1% 10080refresh_pattern -i .(html|htm|css|js)$ 10000 1% 40320   
  #  TAG: read_ahead_gap  buffer-size
  read_ahead_gap 16 KB
   
  #  TAG: negative_ttl    time-units
  negative_ttl 1 minute
   
  # HTTP OPTIONS
  # -----------------------------------------------------------------------------
   
  #  TAG: request_header_max_size    (KB) 
  request_header_max_size 64 KB
   
  #  TAG: request_body_max_size (bytes) 
  request_body_max_size 100 MB
   
  # ADMINISTRATIVE PARAMETERS
  # -----------------------------------------------------------------------------
   
  #  TAG: cache_mgr
  cache_mgr asdafad@abv.bg
   
  #  TAG: visible_hostname
  visible_hostname asdafad.com
   
  # DNS OPTIONS
  # -----------------------------------------------------------------------------
   
  #  TAG: hosts_file
  hosts_file /etc/hosts
   
  #acl QUERY urlpath_regex index ?#no_cache deny QUERY
```

---

### Post by rukiaEnix on 2012-08-10
Why are you saying it is not running if the process is there? I mean what is the reason you don't see it running?

Also please post the log from squid.

---

### Post by SeijiSensei on 2012-08-10
As rukia says, you need to look at /var/log/squid/cache.log.  If squid won't start, you should find the problem there.

---

### Post by DUCKFACE on 2012-08-11
this section here creates a problems 
```
#acl files_allow_administrators_up rep_mime_type –i "/etc/squid3/files_allow_administrators.acl"#acl files_deny_administrators_up rep_mime_type -i "/etc/squid3/files_deny_administrators.acl" #acl files_allow_administrators_down req_mime_type -i "/etc/squid3/files_allow_administrators.acl"#acl files_deny_administrators_down req_mime_type -i "/etc/squid3/files_deny_administrators.acl" #acl files_allow_powerusers_up rep_mime_type -i "/etc/squid3/files_allow_powerusers.acl"#acl files_deny_powerusers_up rep_mime_type -i "/etc/squid3/files_deny_powerusers.acl"#acl files_allow_powerusers_down req_mime_type -i "/etc/squid3/files_allow_powerusers.acl"#acl files_deny_powerusers_down req_mime_type -i "/etc/squid3/files_deny_powerusers.acl" #acl files_allow_users_up rep_mime_type -i "/etc/squid3/files_allow_users.acl"#acl files_deny_users_up rep_mime_type -i "/etc/squid3/files_deny_users.acl"#acl files_allow_users_down req_mime_type -i "/etc/squid3/files_allow_users.acl"  #acl files_deny_users_down req_mime_type -i "/etc/squid3/files_deny_users.acl" 
  #deny_info err_files_administrators_down files_deny_administrators_down 
  #deny_info err_files_powerusers_down files_deny_powerusers_down 
  #deny_info err_files_users_down files_deny_users_down
```

this is the content of deny files
```
^application/x-pn-mpg$
^application/vnd.ms-powerpoint$
^application/asx$
^application/x-mplayer2$
^application/vnd.ms-asf$
^application/x-msn-messenger$
^application/ymsgr$
^multipart/form-data$ 

^video/x-ms-wmv$
^video/mpeg$
^video/mpg$
^video/x-mpg$
^video/mpeg2$
^video/x-mpeg$
^video/x-mpeg2a$
^video/x-ms-asf$
^video/x-ms-asf-plugin$
^video/x-ms-wm$
^video/x-ms-wmx$
^video/x-pn-realvideo$
^video/quicktime$
^video/x-msvideo$
^video/mp4v-es$

^audio/basic$
^audio/x-wav$
^audio/x-mpegurl$
^audio/mpeg$
^audio/x-mpeg$
^audio/mp3$
^audio/x-mp3$
^audio/mpeg3$
^audio/x-mpeg3$
^audio/mpg$
^audio/x-mpg$
^audio/x-mpegaudio$
^audio/x-ms-wma$
^audio/asf$
^audio/vnd.rn-realaudio$
^audio/x-pn-realaudio$
^audio/x-realaudio$
^audio/x-pm-realaudio-plugin$
^audio/x-pn-realvideo$
^audio/x-aiff$
^audio/mp4
```
and this one is alow files
```
^application/txt$
^image/mpg$
```

---

### Post by SeijiSensei on 2012-08-11
Do you mean it won't start if you don't comment out those lines like you have done here?

Is that first line really that long, or are you leaving out some returns along the way?  I've only ever had one ACL per line.

---

### Post by DUCKFACE on 2012-08-12
if i dont comment squid wont work.
thats right its kind of long :D
im gonna try to reduce it but im worried about mime types. are they correct?

another problem i found around. im trying to use dansguardian and squid. with those commented lines squid is working just fine. but when i redirect trafic with iptables to dansguardian ..... there is no traffic at all. from time to time some pages appear but even blocked pages from squid seems to be able for opening. anyone has any idea what happens ?

---

### Post by SeijiSensei on 2012-08-12
As I said, split up that line into separate ones.  One ACL per line.

---

### Post by DUCKFACE on 2012-08-12
it is one acl per line ... its just too long

---

### Post by rukiaEnix on 2012-08-13
I see too many acl in your first line of the config file, and as SeijiSensei says, that's not right, you can't have more than one acl per line

---

