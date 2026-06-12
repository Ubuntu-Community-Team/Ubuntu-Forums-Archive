---
title: "Problem installing Neverball"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by nbakewell on 2008-07-20
Hello everyone,

I am attempting to install my first game and am running across some errors.  I downloaded Neverball and unpacked the tarball using *tar xvzf neverball-1.4.0.tar.gz* to /home/nick/Games.  That all went fine.  So then I opened up the readme and came across:

> Requirements:

    SDL               [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)
    SDL_image         [http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)
    SDL_mixer         [http://www.libsdl.org/projects/SDL_mixer/](http://www.libsdl.org/projects/SDL_mixer/)
    SDL_ttf           [http://www.libsdl.org/projects/SDL_ttf/](http://www.libsdl.org/projects/SDL_ttf/)

So I opened up my package manager and found *libsdl-ttf2.0-0*, *libsdl-image1.2*, and *libsdl-mixer1.2* and installed those.  However, i'm not sure if that is correct - are these the same things the readme is asking for?

Then I called *make*, and got this error:

> make: sdl-config: Command not found
cc -Wall -O3 -ansi  -Ishare -o share/vec3.o -c share/vec3.c
share/vec3.c:15:19: error: stdio.h: No such file or directory
share/vec3.c:16:18: error: math.h: No such file or directory
share/vec3.c: In function &#8216;v_nrm&#8217;:
share/vec3.c:33: warning: implicit declaration of function &#8216;sqrt&#8217;
share/vec3.c:33: warning: incompatible implicit declaration of built-in function &#8216;sqrt&#8217;
share/vec3.c: In function &#8216;m_inv&#8217;:
share/vec3.c:124: warning: implicit declaration of function &#8216;fabs&#8217;
share/vec3.c:124: warning: incompatible implicit declaration of built-in function &#8216;fabs&#8217;
share/vec3.c: In function &#8216;m_rot&#8217;:
share/vec3.c:193: warning: implicit declaration of function &#8216;sin&#8217;
share/vec3.c:193: warning: incompatible implicit declaration of built-in function &#8216;sin&#8217;
share/vec3.c:194: warning: implicit declaration of function &#8216;cos&#8217;
share/vec3.c:194: warning: incompatible implicit declaration of built-in function &#8216;cos&#8217;
make: *** [share/vec3.o] Error 1

Also, right before that the instructions said to execute ./configure, which produced:

> bash: ./configure: No such file or directory

I don't really understand what it is getting at, as you can tell i'm pretty new to Linux.  Are there more packages I need to install, or were those 3 libsdl packages not the correct ones?  I made sure that I was executing these commands from inside of the directory.

---

### Post by Partyboi2 on 2008-07-21
Its in the ubuntu repo's you can install it by add/remove or from terminal
```
sudo apt-get install neverball
```But if you want to compile you  need the dev packages so to compile neverball you will need to install
libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
```
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
```then run 
```
make
```then if there are no errors to run the program
```
./neverball
```

---

### Post by nbakewell on 2008-07-21
Thanks Partyboi2.  Do I need to run ./configure before make, after I install the dev packages?

Also, if the Neverball in the repo is not the current version, how do I go about updating it?  I heard that it was not a good idea trying to update an application downloaded from the repo, and rather uninstall it through add/remove and manually install the full current version by downloading/compiling it.

---

### Post by Partyboi2 on 2008-07-21
> Thanks Partyboi2.  Do I need to run ./configure before make, after I install the dev packages?
No you do not need to run the ./configure command as no is no configure file.
> I heard that it was not a good idea trying to update an application downloaded from the repo, and rather uninstall it through add/remove and manually install the full current version by downloading/compiling it.

That is probably the best way to go about it.

---

### Post by nbakewell on 2008-07-21
Is there any reason why it's better practice to do it that way?  Don't want to mess with where Ubuntu downloads repo files?

---

### Post by Partyboi2 on 2008-07-21
> I heard that it was not a good idea trying to update an application downloaded from the repo
You wouldn't be updating the program from the repo, you would be installing another version of the program. So if you had installed neverball from the repos and then installed neverball by compiling it you would have two neverball programs installed on your system, one from the ubuntu repos and the one you installed from another source.

---

### Post by ffffuuuu on 2009-10-30
Got a bit further by using:
```
sudo apt-get build-dep neverball
```This grabs and installs the dependencies only so that you can try compiling your newer version.

Still didn't work though got:
```
share/fs.c:5:20: error: physfs.h: No such file or directory
share/fs.c:24: error: expected specifier-qualifier-list before ‘PHYSFS_file’
share/fs.c:25: warning: struct has no members
share/fs.c: In function ‘fs_init’:
share/fs.c:29: warning: implicit declaration of function ‘PHYSFS_init’
share/fs.c:31: warning: implicit declaration of function ‘PHYSFS_permitSymbolicLinks’
share/fs.c: In function ‘fs_quit’:
share/fs.c:40: warning: implicit declaration of function ‘PHYSFS_deinit’
share/fs.c: In function ‘fs_error’:
share/fs.c:45: warning: implicit declaration of function ‘PHYSFS_getLastError’
share/fs.c:45: warning: return makes pointer from integer without a cast
share/fs.c: In function ‘fs_base_dir’:
share/fs.c:52: warning: implicit declaration of function ‘PHYSFS_getBaseDir’
share/fs.c:52: warning: return makes pointer from integer without a cast
share/fs.c: In function ‘fs_add_path’:
share/fs.c:57: warning: implicit declaration of function ‘PHYSFS_addToSearchPath’
share/fs.c: In function ‘fs_set_write_dir’:
share/fs.c:62: warning: implicit declaration of function ‘PHYSFS_setWriteDir’
share/fs.c: In function ‘fs_get_write_dir’:
share/fs.c:67: warning: implicit declaration of function ‘PHYSFS_getWriteDir’
share/fs.c:67: warning: return makes pointer from integer without a cast
share/fs.c: In function ‘fs_dir_scan’:
share/fs.c:74: error: ‘PHYSFS_enumerateFiles’ undeclared (first use in this function)
share/fs.c:74: error: (Each undeclared identifier is reported only once
share/fs.c:74: error: for each function it appears in.)
share/fs.c:74: error: ‘PHYSFS_freeList’ undeclared (first use in this function)
share/fs.c: In function ‘fs_open’:
share/fs.c:96: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c:96: warning: implicit declaration of function ‘PHYSFS_openRead’
share/fs.c:100: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c:101: warning: implicit declaration of function ‘PHYSFS_openAppend’
share/fs.c:102: warning: implicit declaration of function ‘PHYSFS_openWrite’
share/fs.c:106: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c:108: warning: implicit declaration of function ‘PHYSFS_setBuffer’
share/fs.c:108: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_close’:
share/fs.c:122: warning: implicit declaration of function ‘PHYSFS_close’
share/fs.c:122: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_mkdir’:
share/fs.c:134: warning: implicit declaration of function ‘PHYSFS_mkdir’
share/fs.c: In function ‘fs_exists’:
share/fs.c:139: warning: implicit declaration of function ‘PHYSFS_exists’
share/fs.c: In function ‘fs_remove’:
share/fs.c:144: warning: implicit declaration of function ‘PHYSFS_delete’
share/fs.c: In function ‘fs_read’:
share/fs.c:151: warning: implicit declaration of function ‘PHYSFS_read’
share/fs.c:151: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_write’:
share/fs.c:156: warning: implicit declaration of function ‘PHYSFS_write’
share/fs.c:156: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_flush’:
share/fs.c:161: warning: implicit declaration of function ‘PHYSFS_flush’
share/fs.c:161: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_tell’:
share/fs.c:166: warning: implicit declaration of function ‘PHYSFS_tell’
share/fs.c:166: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_seek’:
share/fs.c:171: error: ‘PHYSFS_uint64’ undeclared (first use in this function)
share/fs.c:171: error: expected ‘;’ before ‘pos’
share/fs.c:172: error: ‘PHYSFS_sint64’ undeclared (first use in this function)
share/fs.c:172: error: expected ‘;’ before ‘cur’
share/fs.c:173: error: expected ‘;’ before ‘len’
share/fs.c:178: error: ‘pos’ undeclared (first use in this function)
share/fs.c:182: error: ‘cur’ undeclared (first use in this function)
share/fs.c:188: error: ‘len’ undeclared (first use in this function)
share/fs.c:194: warning: implicit declaration of function ‘PHYSFS_seek’
share/fs.c:194: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_eof’:
share/fs.c:199: warning: implicit declaration of function ‘PHYSFS_eof’
share/fs.c:199: error: ‘struct fs_file’ has no member named ‘handle’
share/fs.c: In function ‘fs_length’:
share/fs.c:204: warning: implicit declaration of function ‘PHYSFS_fileLength’
share/fs.c:204: error: ‘struct fs_file’ has no member named ‘handle’
make: *** [share/fs.o] Error 1

```

---

### Post by Partyboi2 on 2009-10-31
If you have not already try installing libphysfs-dev
```
sudo apt-get install libphysfs-dev
```
[B]
[/B]

---

