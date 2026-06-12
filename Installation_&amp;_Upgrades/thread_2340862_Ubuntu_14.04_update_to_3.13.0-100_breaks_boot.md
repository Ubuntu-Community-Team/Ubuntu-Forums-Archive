---
title: "Ubuntu 14.04 update to 3.13.0-100 breaks boot"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by esheesle on 2016-10-22
I just performed an apt-get dist-upgrade and rebooted after it completed successfully.  When the system came back up, i got the grub prompt, and then when it went to boot it just sat with a flashing underline cursor.  I let it sit for several minutes with no change.  I rebooted and chose the old kernel and system booted normally.  Any ideas what might have broken?  No other kernel update has ever caused this for me.

Thanks

---

### Post by esheesle on 2016-10-22
Just to add to this, I've looked at the various dmesg logs and can't find one showing that kernel version attempting to boot, just the previous one .96.

---

### Post by ajgreeny on 2016-10-22
What does terminal command ```
dpkg -l | grep linux-image*
``` show as output?
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by esheesle on 2016-10-23
```

dpkg -l | grep linux-image*
rc  **linux-image**-3.11.0-24-generic                         3.11.0-24.42                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  **linux-image**-3.11.0-26-generic                         3.11.0-26.45                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  **linux-image**-3.13.0-100-generic                        3.13.0-100.147                                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-51-generic                         3.13.0-51.84                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-52-generic                         3.13.0-52.86                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-53-generic                         3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-54-generic                         3.13.0-54.91                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-65-generic                         3.13.0-65.106                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-67-generic                         3.13.0-67.110                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-68-generic                         3.13.0-68.111                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-71-generic                         3.13.0-71.114                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-76-generic                         3.13.0-76.120                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-85-generic                         3.13.0-85.129                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-86-generic                         3.13.0-86.131                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-87-generic                         3.13.0-87.133                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-88-generic                         3.13.0-88.135                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-91-generic                         3.13.0-91.138                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-92-generic                         3.13.0-92.139                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.13.0-93-generic                         3.13.0-93.140                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  **linux-image**-3.13.0-95-generic                         3.13.0-95.142                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  **linux-image**-3.13.0-96-generic                         3.13.0-96.143                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-17-generic                          3.5.0-17.28                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-19-generic                          3.5.0-19.30                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-21-generic                          3.5.0-21.32                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-22-generic                          3.5.0-22.34                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-23-generic                          3.5.0-23.35                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-24-generic                          3.5.0-24.37                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-25-generic                          3.5.0-25.39                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-26-generic                          3.5.0-26.42                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-27-generic                          3.5.0-27.46                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-28-generic                          3.5.0-28.48                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-30-generic                          3.5.0-30.51                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-31-generic                          3.5.0-31.52                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-32-generic                          3.5.0-32.53                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-34-generic                          3.5.0-34.55                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-36-generic                          3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-37-generic                          3.5.0-37.58                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-39-generic                          3.5.0-39.60                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-40-generic                          3.5.0-40.62                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-41-generic                          3.5.0-41.64                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-42-generic                          3.5.0-42.65                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-43-generic                          3.5.0-43.66                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-44-generic                          3.5.0-44.67                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-45-generic                          3.5.0-45.68                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-46-generic                          3.5.0-46.70                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-47-generic                          3.5.0-47.71                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-48-generic                          3.5.0-48.72                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-3.5.0-49-generic                          3.5.0-49.74                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  **linux-image**-3.5.0-51-generic                          3.5.0-51.76                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.11.0-24-generic                   3.11.0-24.42                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.11.0-26-generic                   3.11.0-26.45                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  **linux-image**-extra-3.13.0-100-generic                  3.13.0-100.147                                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-36-generic                   3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-51-generic                   3.13.0-51.84                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-53-generic                   3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-54-generic                   3.13.0-54.91                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-65-generic                   3.13.0-65.106                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-67-generic                   3.13.0-67.110                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-68-generic                   3.13.0-68.111                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-71-generic                   3.13.0-71.114                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-76-generic                   3.13.0-76.120                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-85-generic                   3.13.0-85.129                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-86-generic                   3.13.0-86.131                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-87-generic                   3.13.0-87.133                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-88-generic                   3.13.0-88.135                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-91-generic                   3.13.0-91.138                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-92-generic                   3.13.0-92.139                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.13.0-93-generic                   3.13.0-93.140                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  **linux-image**-extra-3.13.0-95-generic                   3.13.0-95.142                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  **linux-image**-extra-3.13.0-96-generic                   3.13.0-96.143                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-17-generic                    3.5.0-17.28                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-19-generic                    3.5.0-19.30                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-21-generic                    3.5.0-21.32                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-22-generic                    3.5.0-22.34                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-23-generic                    3.5.0-23.35                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-24-generic                    3.5.0-24.37                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-25-generic                    3.5.0-25.39                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-26-generic                    3.5.0-26.42                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-27-generic                    3.5.0-27.46                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-28-generic                    3.5.0-28.48                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-30-generic                    3.5.0-30.51                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-31-generic                    3.5.0-31.52                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-32-generic                    3.5.0-32.53                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-34-generic                    3.5.0-34.55                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-36-generic                    3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-37-generic                    3.5.0-37.58                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-39-generic                    3.5.0-39.60                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-40-generic                    3.5.0-40.62                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-41-generic                    3.5.0-41.64                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-42-generic                    3.5.0-42.65                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-43-generic                    3.5.0-43.66                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-44-generic                    3.5.0-44.67                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-45-generic                    3.5.0-45.68                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-46-generic                    3.5.0-46.70                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-47-generic                    3.5.0-47.71                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-48-generic                    3.5.0-48.72                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  **linux-image**-extra-3.5.0-49-generic                    3.5.0-49.74                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  **linux-image**-extra-3.5.0-51-generic                    3.5.0-51.76                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  **linux-image**-generic                                   3.13.0.100.108                                      amd64        Generic Linux kernel image

```

---

