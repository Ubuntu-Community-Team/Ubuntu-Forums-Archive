---
title: "Data Recovery with PhotoRec help"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-05-30
Hi everybody!

I am running a liveCD and trying to recover data stored by windows xp on the HD of my laptop. I want to write all the data to an external hard drive.
I've turned off swap.
I have got Photorec up and running and it successfully detects my TB external and 100GB internal hard drive.

The problem is that Photorec does not offer me any option to save to the external once I have selected the internal hard drive. Does anybody know what is going on?

I get offered this menu:

```

PhotoRec 6.11, Data Recovery Utility, April 2009                                
Christophe GRENIER <grenier@cgsecurity.org>                                     
http://www.cgsecurity.org                                                       
                                                                                
Do you want to save recovered files in /home/ubuntu ? [Y/N]                     
Do not choose to write the files to the same partition they were stored on.     
                                                                                
To select another directory, use the arrow keys.                                
drwxr-xr-x   999   999       580 30-May-2010 15:40 .                            
drwxr-xr-x     0     0        60 30-May-2010 16:14 ..                           
drwxr-xr-x   999   999        80 30-May-2010 16:16 Desktop                      
drwxr-xr-x   999   999        40 30-May-2010 16:15 Documents                    
drwxr-xr-x   999   999        40 30-May-2010 16:15 Downloads                    
drwxr-xr-x   999   999        40 30-May-2010 16:15 Music                        
drwxr-xr-x   999   999        40 30-May-2010 16:15 Pictures                     
drwxr-xr-x   999   999        40 30-May-2010 16:15 Public                       
drwxr-xr-x   999   999        40 30-May-2010 16:15 Templates                    
drwxr-xr-x   999   999        40 30-May-2010 16:15 Videos                       
-rw-r--r--   999   999     40960 30-May-2010 15:40 photorec.ses                 
                                                                                
                                                                                
                                                                 
```

and if I press 'N' it just sends me back to here:

```


PhotoRec 6.11, Data Recovery Utility, April 2009                                
Christophe GRENIER <grenier@cgsecurity.org>                                     
http://www.cgsecurity.org                                                       

                                                                                
Disk /dev/sda - 100 GB / 93 GiB (RO) - ATA HTS541010G9SA00                      
                                                                                
     Partition                  Start        End    Size in sectors             
     No partition             0   0  1 12161  80 63  195371568 [Whole disk]     
 1 * Linux                    0  32 33 11790 176 34  189415424                  
 2 E extended             11790 209  2 12161  72  7    5951490                  
 5 L Linux Swap           11790 209  4 12161  72  7    5951488                  
                                                                                
                                                                                
                                                                                
                                                                 
```

How do I tell it to use my external as the destination!

---

### Post by goseph on 2010-05-30
sorted now!

I navigated to the external in Dolphin and ran photoRec again and it somehow picked up the external this time round when it came to selecting data destination.

---

