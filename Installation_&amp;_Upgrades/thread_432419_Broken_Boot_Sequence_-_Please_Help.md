---
title: "Broken Boot Sequence - Please Help"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by jerremy-tamlin on 2007-05-04
I have broken my boot sequence during an upgrade from Dapper to Edgy.

When running kernal 2.6.15-28-386  (recovery mode)
My Laptop hangs after:

```
[17179578.528000] kjournald starting. Commit interval 5 seconds
[17179578.528000] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.

```


When running kernal 2.6.15-27-386  (recovery mode)
it does things in a slightly different order but still hangs after:

```
[17179578.528000] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
[17179578.528000] kjournald starting. Commit interval 5 seconds
Done.

```

Can any one tell me how to fix this?
A friend of mine thought it might be a problem with the journal as all my partitions are ext3.
I don't know what these scripts are supposed to do but as I broke my installation by crashing my comp half way through an upgrade I think it faily likely that it's an issue with a script pointing to something that doesn't exist yet or running something that isn't set up correctly.

Thanks to anyone who can help.
I started a thread earlier but no one has replied, hopefully with this more specific problem someone will have some Ideas.

---

