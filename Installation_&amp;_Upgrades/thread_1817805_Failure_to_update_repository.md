---
title: "Failure to update repository"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by jacob.harris9799 on 2011-08-03
Hello all!

having somewhat of an issue when it comes to updating through Update Manager.

I get "Failed to download repository information

Check your Internet connection."

        details :W:Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge./ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/jonoomph/openshot-edge./ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge./ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/jonoomph/openshot-edge./ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Running 11.04, no major modifications.

I will try to be as helpful as possible.

also, I believe I have a few hard drive faults- I have reformatted several times, but I still have issues in the boot process.

---

### Post by gordintoronto on 2011-08-03
Run System/Administration/Synaptic Package Manager. Select Settings/Repositories. "jonoomph" probably appears under Other Software; unselect those two repositories. Click OK, then Reload. Update Manager should be OK.

---

### Post by JYx70 on 2011-08-04
I had the same problem with another repository:
[http://ppa.launchpad.net/ubun-student/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubun-student/ppa/ubuntu/dists/natty/main/source/Sources)
and:     ...natty/main/binary-i386/Packages

I unchecked these in syn-pack >settings>repositories>other software

update manager is now working with no problems

---

