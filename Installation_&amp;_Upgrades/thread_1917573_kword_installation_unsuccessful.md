---
title: "kword installation unsuccessful"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2012-01-30
I am trying to install kword 

```

sudo aptitude install kword
The following NEW packages will be installed:
  akonadi-backend-mysql{a} akonadi-server{a} create-resources{a} 
  freetds-common{a} kdepim-runtime{a} kdepimlibs-kio-plugins{a} kexi{a} 
  koffice-data{a} koffice-libs{a} kspread{a} kword kword-data{a} 
  libakonadi-contact4{a} libakonadi-kabc4{a} libakonadi-kcal4{a} 
  libakonadi-kde4{a} libakonadi-kmime4{a} libakonadiprotocolinternals1{a} 
  libdmtx0a{a} libgsf-1-114{a} libgsf-1-common{a} libgsl0ldbl{a} 
  libkabc4{a} libkcal4{a} libkcalcore4{a} libkcalutils4{a} libkimap4{a} 
  libkldap4{a} libkmbox4{a} libkmime4{a} libkpimidentities4{a} 
  libkpimtextedit4{a} libkpimutils4{a} libkresources4{a} libkrossui4{ab} 
  libmailtransport4{a} libmicroblog4{a} libpq5{a} libpqxx-3.0{a} 
  libprison0{a} libqrencode3{a} libreadline5{a} libruby1.8{a} libspnav0{a} 
  libsybdb5{a} libxbase2.0-0{a} mysql-client-core-5.1{a} 
  mysql-server-core-5.1{a} ruby{a} ruby1.8{a} 
0 packages upgraded, 50 newly installed, 0 to remove and 3 not upgraded.
Need to get 27.9 MB of archives. After unpacking 113 MB will be used.
The following packages have unmet dependencies:
  libkrossui4: Depends: libkdecore5 (= 4:4.7.1-0ubuntu3) but 4:4.7.2-0ubuntu2 is installed.
               Depends: libkdeui5 (= 4:4.7.1-0ubuntu3) but 4:4.7.2-0ubuntu2 is installed.
               Depends: libkio5 (= 4:4.7.1-0ubuntu3) but 4:4.7.2-0ubuntu2 is installed.
               Depends: libkparts4 (= 4:4.7.1-0ubuntu3) but 4:4.7.2-0ubuntu2 is installed.
               Depends: libkrosscore4 (= 4:4.7.1-0ubuntu3) but 4:4.7.2-0ubuntu2 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     kexi [Not Installed]                               
2)     koffice-libs [Not Installed]                       
3)     kspread [Not Installed]                            
4)     kword [Not Installed]                              
5)     libkrossui4 [Not Installed]                        



Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

after this nothing happens.
I also tried

```
sudo aptitude install -f
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```                                         
but even here things fail.

I have also tried apt-get
```

sudo apt-get install kword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kword : Depends: koffice-libs (>= 1:2.3.3-0ubuntu6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by jerrrys on 2012-02-01
Your running u11.10; wish you would of posted that.  Try:

sudo apt-get update

---

### Post by jamesbon on 2012-02-01
Yes I did that update thing but the error is still there.

---

### Post by jerrrys on 2012-02-01
Hi James

And no errors when you did the update thing?

I just installed kword in 11.10 without problem.  Whats your software sources look like?  In terminal:

gedit /etc/apt/sources.list

Are you using the "main server" for downloads?

---

