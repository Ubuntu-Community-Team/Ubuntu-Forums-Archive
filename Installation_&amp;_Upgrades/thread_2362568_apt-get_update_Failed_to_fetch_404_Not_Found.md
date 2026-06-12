---
title: "apt-get update Failed to fetch 404 Not Found"
date: 2017-05-30
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2017-05-30
I am encountering the error when doing ```
sudo apt-get update
```. 
How can I fix this issue?

```
Ign:49 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 Packages
Ign:50 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main i386 Packages
Ign:51 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main all Packages
Ign:52 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en_SG
Ign:53 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en                                                                
Ign:54 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 DEP-11 Metadata                                                         
Ign:55 http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main DEP-11 64x64 Icons                                                            
Ign:49 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 Packages                                                  
Ign:50 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main i386 Packages                                                   
Ign:51 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main all Packages                                                    
Ign:52 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en_SG                                               
Ign:49 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 Packages                                                  
Ign:55 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main DEP-11 64x64 Icons                                              
Ign:50 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main i386 Packages                                                   
Ign:53 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en                                                  
Ign:51 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main all Packages                                                    
Ign:52 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en_SG                                               
Ign:54 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 DEP-11 Metadata                                           
Ign:55 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main DEP-11 64x64 Icons                                              
Ign:49 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 Packages                                                  
Ign:50 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main i386 Packages                                                   
Ign:53 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en                                                  
Ign:51 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main all Packages                                                    
Ign:52 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en_SG                                               
Ign:54 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 DEP-11 Metadata                                           
Ign:55 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main DEP-11 64x64 Icons
Ign:49 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 Packages
Ign:50 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main i386 Packages
Ign:51 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main all Packages
Ign:53 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en
Ign:52 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en_SG
Ign:55 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main DEP-11 64x64 Icons
Ign:54 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 DEP-11 Metadata
Err:49 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:50 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main i386 Packages
Ign:51 http://103.1.138.199/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main all Packages
Ign:53 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en
Ign:52 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main Translation-en_SG
Ign:54 http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial/main amd64 DEP-11 Metadata
Fetched 4,300 kB in 17s (241 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/canonical-x/vulkan/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/canonical-x/vulkan/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://103.1.138.154/ppa.launchpad.net/canonical-x/vulkan/ubuntu/dists/xenial/main/dep11/icons-64x64.tar  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by deadflowr on 2017-05-30
I see no such ppa anywhere.
I see canonical-x/x-staging, for xenial.
And canonical-x-testing for zesty.
But I do not see any canonical-x/vulkan ppa anywhere.

do you remember how you added it?

---

### Post by sunbear-c22 on 2017-05-30
I just checked debian packages 

dpkg -l | grep vulkan
ii  libvulkan1:amd64                           1.0.46.0+dfsg1-1~gpu16.04.1                   amd64        Vulkan loader library
ii  mesa-vulkan-drivers                        12.0.6-0ubuntu0.16.04.1                       amd64        Mesa Vulkan graphics drivers
ii  vulkan-utils                               1.0.46.0+dfsg1-1~gpu16.04.1                   amd64        Miscellaneous Vulkan utilities

I then used Synaptic to purge these packages. After that, I re-ran sudo apt-get update but still received the same errors. 
Presently, I have locally installed LunarG VulkanSDK in my folder.

Based on your reply I just realized the error is caused by the ppa related to Vulkan. [http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu](http://103.1.138.206/ppa.launchpad.net/canonical-x/vulkan/ubuntu). Can't remember how it was added. But I have removed it and the error is no more. Thanks.

---

### Post by deadflowr on 2017-05-30
> Can't remember how it was added
It's possible, depending on how long ago it was added, to find it in your history if you added through the terminal:
```
history | grep ppa
```
should show all commands you ran with ppa in them, one of which may be the command you ran to add the ppa.

You might also be able to re-add the x-staging ppa, which itself contains vulkan packages.
Get that one from here:
[https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging]("https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging")

---

### Post by sunbear-c22 on 2017-05-30
Thanks for the pointers. I had check the links and noticed the vulkan version is fairly older. It is version 1.0.49.0 now instead of 1.0.42.0 that is provided in the link. Will stick to using LunarG's Vulkan SDK.

---

