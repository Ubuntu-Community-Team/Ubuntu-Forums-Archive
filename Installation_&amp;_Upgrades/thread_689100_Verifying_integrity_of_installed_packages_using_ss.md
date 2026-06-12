---
title: "Verifying integrity of installed packages using ssl connected &quot;official&quot; hashes"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by joeljose420 on 2008-02-06
U may call me paranoid..but i just wanted to keep my system "clean". I was thinking of potential threats the ubuntu cd has while shipping..and also man-in-the-middle attacks during apt-get or synaptic methods of package installs.. even users like me, do install from "unofficial" ways like websites...especially when ubuntu doesnt have that package in its repo...

a central repo of hashes of all "ubuntu" packages would be very helpful...all universe,multiverse..oficial..etc.. 

and if ssl connection was used...i think man-in-the-middle can be avoided....

i may be wrong here..many existing methods may exist and be more efficient.. please enlighten me..as i look fprward to secure my system...

P.S: gov can track me using my phone and satellite and the car parked just outside my door...but i dont want to let it "litter" my ubuntu.

---

### Post by zvacet on 2008-02-06
I don´t know if my answer will be good enough for you but let´s try.There is no man-in-the-middle.By synaptic or apt-get you are connecting to the Ubuntu main server and all packages are put there by Ubuntu devel team.Of course you can use local server but what they are realy do is just mirroring main sever content with addition of some packages(like language locale packages).For unofficial repos I think medibuntu is good choice.It is another security option.Plug off your comp,hide it at some place where nobody can find it and lock it.If you don´t do that you will never be 100% secure,because there is no such thing.

---

### Post by matik on 2008-02-11
Well, i have same problem. Not because i'm paranoid - oh no
I just managed to scew up some parts of filesystem when experimenting with hibernate on T60. i just loaded previous hibernate image from disk somehow and restarted. after restart fsck started to complain and then i thought - in hibernate image the journal and file tables were not in sync with real disk anymore. so i ended up fsck-ing for some time. I can boot now, most stuff works, but i'm sure some packages are damaged too.
I found out what there is little proggie called debsums which checks the hashes so i reinstalled some failed packages one-by-one. too bad not all packages have hashes... :(
It would be really nice if someone could write a script which automatically reinstalls damaged ones. Although, maybe it does not get lots of use, not many people are able to screw up filesystems that way :P

---

