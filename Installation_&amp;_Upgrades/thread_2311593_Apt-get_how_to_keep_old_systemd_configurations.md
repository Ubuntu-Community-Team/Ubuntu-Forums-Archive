---
title: "Apt-get: how to keep old systemd configurations"
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by petwri on 2016-01-28
Hi there!

For one of the services I have running, I use a customized systemd-configuration file. How do I tell apt-get to keep this local version I have and don't replace it with the maintainers systemd file after an 'apt-get upgrade'?

Thanks for the help!

---

### Post by steveo314 on 2016-02-01
you could make a copy of it and then after it gets overwritten overwrite the maintainer's config with your config. Unless it is one of the packages that actually asks you which you want to use. Still make a backup either way.

---

### Post by petwri on 2016-02-01
Yes, of course this is possible. But I was asking for a solution where I would not need to manually replace the config file after every upgrade.

---

### Post by matt_symes on 2016-02-01
Hi

I was reading about this the other day.

Take a look at

```
sudo systemctl edit <systemd unit>
```

From the man page
```

       edit NAME...                                                                                                           
           Edit a drop-in snippet or a whole replacement file if --full is specified, to extend or override the specified     
           unit.                                                                                                              
                                                                                                                              
           Depending on whether --system (the default), --user, or --global is specified, this command creates a drop-in      
           file for each unit either for the system, for the calling user, or for all futures logins of all users. Then,      
           the editor (see the "Environment" section below) is invoked on temporary files which will be written to the        
           real location if the editor exits successfully.                                                                    
                                                                                                                              
           If --full is specified, this will copy the original units instead of creating drop-in files.                       
                                                                                                                              
           If --runtime is specified, the changes will be made temporarily in /run and they will be lost on the next          
           reboot.                                                                                                            
                                                                                                                              
           If the temporary file is empty upon exit, the modification of the related unit is canceled.                        
                                                                                                                              
           After the units have been edited, systemd configuration is reloaded (in a way that is equivalent to                
           daemon-reload).                                                                                                    
                                                                                                                              
           Note that this command cannot be used to remotely edit units and that you cannot temporarily edit units which
           are in /etc, since they take precedence over /run.
```

I can't really give you much more than this as i have not tried it but it does give you a place to start reading up.

I have been reading up on it for when i switch most of my machines over to 16.04 in the latter half of this year.

Kind regards

---

