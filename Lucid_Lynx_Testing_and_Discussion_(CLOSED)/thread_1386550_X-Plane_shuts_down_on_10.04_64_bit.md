---
title: "X-Plane shuts down on 10.04 64 bit"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-01-20
Trying to get X-Plane running on 10.04 64 bit it shuts down with the following errors.

Kicking off async tex load.
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  5193
  Current serial number in output stream:  5224
AL lib: ALc.c:1368: exit(): closing 1 Device
AL lib: ALc.c:1345: alcCloseDevice(): destroying 1 Context
[Thread 0xec7d5b70 (LWP 2743) exited]
[Thread 0xecfd6b70 (LWP 2742) exited]
[Thread 0xf7a28b70 (LWP 2741) exited]

Program exited with code 01.

X-Plane on 10.04 32 bit is running fine other than a DVD mounting problem.

Bill

---

### Post by dagrump on 2010-01-20
Is this the x-plane 9 windows game? Are you running it with wine? I have that game I haven't even opened it. I wouldn't of even thought to try running it on linux.
I'll watch to see what happens with this thread, I might try to get in running on something if I get time. I always enjoyed the old strike eagle games, of course some times I bombed the wrong folks, that's the breaks.

---

### Post by sparker256 on 2010-01-20
> **dagrump said:**
> Is this the x-plane 9 windows game? Are you running it with wine? I have that game I haven't even opened it. I wouldn't of even thought to try running it on linux.
I'll watch to see what happens with this thread, I might try to get in running on something if I get time. I always enjoyed the old strike eagle games, of course some times I bombed the wrong folks, that's the breaks.

This is a flight simulator that runs on Linux, Mac, and Windows and version that I am using is for Linux.

Bill

---

### Post by dagrump on 2010-01-20
Sorry I forgot some people don't like it when you call a flight sim a game, I would bet it is the same thing I have but I don't have a native version.
This thing has 60 gig of scenery & over 30 aircraft. I guess I'll have to see if they have an installer to load the windows version on linux. Please don't take it wrong that I called it a game.

Edit:
Installation for linux on the support page even from retail disks, looks promising, installer even? Looks interesting.

---

### Post by ato on 2010-01-24
Same problem for me with Quake Wars (native) and doom 3 doesn't start too.
Doom 3 show me this info
```
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
```

Others opengl apps works fine

I think there's something wrong with nvidia driver

---

### Post by anthony.hook on 2010-03-24
This is marked "resolved," what was the final resolution?

---

### Post by sparker256 on 2010-03-24
> **anthony.hook said:**
> This is marked "resolved," what was the final resolution?

I was running a very early alpha version and it became resolved in later builds. I can presently run X-Plane 9.45 or 9.50 on either Ubuntu 10.04 32 or 32 bit.

Bill

---

