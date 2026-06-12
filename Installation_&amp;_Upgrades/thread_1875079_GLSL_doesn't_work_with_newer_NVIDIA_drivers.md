---
title: "GLSL doesn't work with newer NVIDIA drivers"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by oaschal on 2011-11-04
Hi there,

I've recently updated the NVIDIA gpu drivers from
NVIDIA-Linux-x86_64-195.36.31-pkg2.run
to
NVIDIA-Linux-x86_64-260.19.12.run
NVIDIA-Linux-x86_64-285.05.09.run

With the newer drivers my GLSL programs showed different and wrong behaviour.

E.g. the following code produces something different (nothing really logical though)
```

vec4 foo(){

  // some code ...

  if(a<b)
    return vec4(0.0,0.0,0.0,1.0);

  // some code modifying vec4 result

  return result;

}

```
then
```

vec4 foo(){

  // some code ...

  if(a<b){
    result = vec4(0.0,0.0,0.0,1.0);
  }else{

    // some code modifying vec4 result
  }

  return result;

}

```



For the old driver both versions work fine (as they should).
But with the newer ones only the second works.
I had similar wrong behaviour with nested loops. With the newer drivers I had to unwrap the loops (write down every possible value) to make it working.

Any idea whats wrong with the new drivers? There were no error messages / warnings from OpenGL nor GLSL

My system:
Ubuntu 10.04 (64bit)
Kernel Linux 2.6.32-34-generic
GeForce GTX 285

---

