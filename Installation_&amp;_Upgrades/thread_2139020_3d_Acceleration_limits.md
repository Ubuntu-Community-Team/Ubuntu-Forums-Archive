---
title: "3d Acceleration limits?"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2013-04-25
When I upgraded to 13.04, the display on my two 1960x1024 monitors were limited to a maximum of 3d hardware accelleration for the combination of (1024, 1024).  The two displays appeared as mirrored (they were not before the upgrade).  When I attempted to unclick the mirror setting on the display, that failed after a timeout and reported that the 3d acceleration was limited to 1024 x 1024.

I was able to resolve this by shutting down VirtualBox, change the settings to remove the 3d acceleration and then restart the virtual machine.  All is now back to normal, but I cannot enable the 3d acceleration without corrupting the displays (no launch pad, etc.).

Has anyone else seen this problem and do you have a solution?  The host machine is running Windows 7 64bit with a ATI Radeon HD 5700 Series card.  WOULD a different card make any difference? although the current one meets my needs, except this issue.  I also reinstalled the Guest additions -- but saw no improvement.

I would love to enable the 3d acceleration.  Without that, the display etc. is usable.  I see:
glxgears: ~ 530 FPS
And unity_support_test -p reports:
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
libGL error: failed to load driver: vboxvideo
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string:  2.1 Mesa 9.1.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

as expected.

Othewise, I find the improvements in this release to be excellent!  Thanks for all the hard work. - it's nice to move further and further away from Windoz.

Any help would be greatly appreciated.

---

### Post by joel@parke.ods.org on 2013-04-30
Bump -- has anyone else seen this, where one cannot enable 3d hardware acceleration in Virtualbox when hosting on windoz?  
Thanks!

> **JoelParke said:**
> When I upgraded to 13.04, the display on my two 1960x1024 monitors were limited to a maximum of 3d hardware accelleration for the combination of (1024, 1024).  The two displays appeared as mirrored (they were not before the upgrade).  When I attempted to unclick the mirror setting on the display, that failed after a timeout and reported that the 3d acceleration was limited to 1024 x 1024.

I was able to resolve this by shutting down VirtualBox, change the settings to remove the 3d acceleration and then restart the virtual machine.  All is now back to normal, but I cannot enable the 3d acceleration without corrupting the displays (no launch pad, etc.).

Has anyone else seen this problem and do you have a solution?  The host machine is running Windows 7 64bit with a ATI Radeon HD 5700 Series card.  WOULD a different card make any difference? although the current one meets my needs, except this issue.  I also reinstalled the Guest additions -- but saw no improvement.

I would love to enable the 3d acceleration.  Without that, the display etc. is usable.  I see:
glxgears: ~ 530 FPS
And unity_support_test -p reports:
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
libGL error: failed to load driver: vboxvideo
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string:  2.1 Mesa 9.1.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

as expected.

Othewise, I find the improvements in this release to be excellent!  Thanks for all the hard work. - it's nice to move further and further away from Windoz.

Any help would be greatly appreciated.

---

