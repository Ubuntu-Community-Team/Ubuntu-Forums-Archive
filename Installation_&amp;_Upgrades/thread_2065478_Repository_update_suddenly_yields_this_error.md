---
title: "Repository update suddenly yields this error:"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by Nihilistical on 2012-10-02
Fetched 25.3 MB in 16s (1,579 kB/s)                                            
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

i tried an apt-get clean thing i found on the forum, but to no effect. i am still getting some updates. should i just removed these from the repos list?

---

### Post by stinkeye on 2012-10-02
The ppa only has packages up to Natty and your looking for Precise packages.
Just remove using **software sources > other software**

---

### Post by jerrrys on 2012-10-02
Welcome to the forums :)

this may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources+list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources+list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)
[]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources+list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by daslinkard on 2012-10-02
Did Jerrys suggestion work for you?

---

