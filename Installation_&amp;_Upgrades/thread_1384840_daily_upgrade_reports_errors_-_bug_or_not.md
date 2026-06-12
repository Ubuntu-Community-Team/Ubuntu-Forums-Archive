---
title: "daily upgrade reports errors - bug or not?"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by tjk on 2010-01-18
Earlier today I did an upgrade and while processing the following error occurred: (I have commented with [COLOR=Red]red[/COLOR] and made the questionable error text **bold**)
----------------------
The following packages will be upgraded:                                                                  
  cpp-4.4 g++-4.4 gcc-4.4 gcc-4.4-base lib32gcc1 lib32mudflap0 lib32stdc++6 libgcc1 libgfortran3 libgomp1 libpurple0 libstdc++6
  libstdc++6-4.4-dev libthai-data libthai0 pidgin pidgin-data                                                                  
[COLOR=Red]... (I deleted most of the download & install lines) [/COLOR]                                                                     
Processing triggers for hicolor-icon-theme ...                                                            
[B]kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so                                       
                                                                   <unknown program name>(4732)/ KStartupInfo::createNewStartupId: creating:  "kubuntu64;1263866422;300982;4732_TIME0" : "unnamed app"                                                                                      
                                                        kbuildsycoca4 running...                                                              
                                                                                Error: "/var/tmp/kdecache-timaWMe5N" is owned by uid 1000 instead of uid 0.       [/B]                                                                                                                          
             Processing triggers for menu ...                                                                                                 
Processing triggers for desktop-file-utils ...                                                                                                
Setting up ... [COLOR=Red](deleted long list of setups)[/COLOR]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
[B]kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
<unknown program name>(4732)/ KStartupInfo::createNewStartupId: creating:  "kubuntu64;1263866448;70421;4732_TIME0" : "unnamed app"
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-timaWMe5N" is owned by uid 1000 instead of uid 0[/B].
---------------------------
Should I be concerned with these errors?  Should I report this as a bug?

---

