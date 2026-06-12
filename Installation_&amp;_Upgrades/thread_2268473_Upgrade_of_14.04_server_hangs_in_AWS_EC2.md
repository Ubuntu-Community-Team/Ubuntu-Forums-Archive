---
title: "Upgrade of 14.04 server hangs in AWS EC2"
date: 2015-03-09
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2015-03-09
while doing an upgrade there is a console prompt by a grub package that is causing a hang in AWS EC2:

 ```
A new version of /boot/grub/menu.lst is available, but the version installed currently has been locally modified.  &#9474;     
&#9474;                                                                                                                    &#9474;
&#9474; What would you like to do about menu.lst?                                                                          &#9474;
&#9474;                                                                                                                    &#9474;
&#9474;                             install the package maintainer's version                                               &#9474;
&#9474;                             keep the local version currently installed                                             &#9474;     
&#9474;                             show the differences between the versions                                              &#9474;     
&#9474;                             show a side-by-side difference between the versions                                    &#9474;     
&#9474;                             show a 3-way difference between available versions                                     &#9474;     
&#9474;                             do a 3-way merge between available versions (experimental)                             &#9474;     
&#9474;                             start a new shell to examine the situation                                             &#9474;     
&#9474;                                                                                                                    &#9474;     
&#9474;                                                                                                                    &#9474;     
&#9474;                                                       <Ok>    
```

pre-feeding a carriage return does not work around this.
is there a way to bypass prompts like this to allow background upgrades?

---

