---
title: "make-kpkg kernel compile question"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by beebelo on 2005-11-15
Here's a question I have because I've been reading too many HOWTOs!

The following commands are from three different sources--all HOWTOs on compiling an Ubuntu kernel from Ubuntu sources.  

```

[SIZE="2"]make-kpkg --initrd --append-to-version=-custom kernel_image modules_image
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
make-kpkg --initrd --append-to-version-.custom kernel_image binary[/SIZE]
```

These three command lines occur at the same time in the process -- "Now it's time to make the kernel package.  You will end up with a .deb file you can install just like any Ubuntu package", etc.

Why are they different, and what effects do the differences have?

Thanks.

---

