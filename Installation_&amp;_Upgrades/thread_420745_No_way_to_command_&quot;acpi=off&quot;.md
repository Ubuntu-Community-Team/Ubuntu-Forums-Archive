---
title: "No way to command &quot;acpi=off&quot;"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by 96west on 2007-04-23
Further tests confirm that the Ubuntu install disks including the alternate go into error failure before offering me any way to command "acpi=off" which was needed to make the Freespire and Puppy installers work. Seems several in the forums have had various acpi=off issues. This is a 4 year old Compaq. If there is no workaround to this I guess I can't have Ubuntu, unless I buy a new PC. Though this one works fine otherwise.

---

### Post by thelinuxguy on 2007-04-23
Have you tried using noapic leaving the acpi settings unchanged? They are not related but passing the noapic kernel parameter seems to have worked for many, including mine.

Some more info here: [https://answers.launchpad.net/ubuntu/+question/4506](https://answers.launchpad.net/ubuntu/+question/4506)
Take a look here as well: [http://wiki.linuxquestions.org/wiki/APIC](http://wiki.linuxquestions.org/wiki/APIC)

---

