---
title: "Problem Setting Up Dedicated Counter-Strike Source Server"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2011-01-07
even though I have set the .bin file to have executable permissions, it still gives me a "Permission Denied" error when I try to execute it.

I'm completely befuddled.  Does anyone have any ideas?  Even if I try to execute it as root, I get a permission denied error.

Please see below:

```

css@Suppository:~/srcds$ wget http://storefront.steampowered.com/download/hldsupdatetool.bin
--2011-01-07 21:42:03--  http://storefront.steampowered.com/download/hldsupdatetool.bin
Resolving storefront.steampowered.com... 208.111.129.60, 68.142.91.151
Connecting to storefront.steampowered.com|208.111.129.60|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3513408 (3.4M) [application/octet-stream]
Saving to: `hldsupdatetool.bin'

100%[======================================>] 3,513,408   1.05M/s   in 3.2s    

2011-01-07 21:42:06 (1.05 MB/s) - `hldsupdatetool.bin' saved [3513408/3513408]
css@Suppository:~/srcds$ chmod +x hldsupdatetool.bin 
css@Suppository:~/srcds$ ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: Permission denied
```

Thanks,
Matt

---

