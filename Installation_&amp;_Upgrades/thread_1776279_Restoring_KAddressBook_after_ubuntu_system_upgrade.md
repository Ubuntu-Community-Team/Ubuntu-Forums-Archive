---
title: "Restoring KAddressBook after ubuntu system upgrade"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by Trent T on 2011-06-05
Problem: How I Lost My Addresses

In June 2011, I received the sad news that Ubuntu 9.10 would no longer be supported.  It was time to move on to Ubuntu 10.whatever, which had been offering itself to me via the Update Manager for at least a year.

After doing a complete backup, I ran the update overnight.  Ubuntu 10.04 was on my computer the next morning.  
While poking around, I noticed that the Kontact KAddressBook had no entries;
Instead, I had display with three columns;
Column #1, "Address Books" had the cryptic entry 'std.vcf' :confused:  Clicking on it did nothing.  Apparently, all my addresses were gone.

Solution: Finding and Reloading the Addresses

My addresses were in the vCard format, located in 

/home/MYUSERNAME/.kde/share/apps/kabc/std.vcf

After checking to see that my backup file of std.vcf was the same size as the system file, I did the following, modified from instructions provided by Joao G. Peixoto joaogpeixoto (thread Ubuntu Kmail Kaddressbook -- Thanks Joao!);

Within the Kontact KAddressBook, I deleted the empty std.vcf addressbook;
Edit
    Delete Address Book

Then I generated a new address book to hold my addresses;

File
   New
      Add Address Book

KDE Address Book (Traditional)

Select a KDE Plugin
    File
       Next

Format: vCard
Location: /home/MYUSERNAME/.kde/share/apps/kabc/std.vcf

The [next] command took me back to the 3 empty columns.
In a minute or two, 'Names' (column 2) began to fill up with my old contact listings--
Back in business! :guitar:

---

### Post by smoo2 on 2011-06-06
Thanks for this! I had nearly exactly the same problem, and solved it with your hints. Very helpful.

---

