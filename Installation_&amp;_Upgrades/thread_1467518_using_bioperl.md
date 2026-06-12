---
title: "using bioperl???"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ChParker on 2010-04-30
Hopefully someone can help. I installed bioperl using the Synaptic Package Manager and it seemed to install fine. But now I have no idea how to use it. My normal perl programs run fine with just a shebang line, but when I tried this simple program (the one they recommend to get you going):

#!/usr/bin/perl -w

use Bio::Seq;

$seq_obj = Bio::Seq->new(-seq => "aaaatfffffffffccccgtt",
                                 -alphabet => 'dna' );
                                
print @seq_obj->seq;


I got this output:

"Can't call method "seq" without a package or object reference at ./file.pl line 10."


I know its a stupid question, but how do I use this program? Any help would be greatly appreciated, as I'm new to this and trying to learn.

thanks.

---

### Post by Suhaib58 on 2010-12-03
I have installed Bioperl 1.6.1 through Synaptic package manger. I am facing the same problem. Is there any way to troubleshoot this problem.

---

