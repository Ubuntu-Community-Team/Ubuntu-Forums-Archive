---
title: "g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1 gives strange error while compiling"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by souvik.datta on 2011-12-20
Hello,
I had been using ubuntu 10.10 for quite some time as my development PC. My code was to build without error with g++ version 4.4.5. Recently I had upgraded my system to 11.10 which has come with g++ version 4.6.1
Now , using this compiler, when I am trying to build the same piece of code, I am getting this error:

g++: error: unrecognized option ‘--end-group’

The Make file line, where this error is thrown is:

$(TARGET): $(OBJS)
        g++ $(LDFLAGS)  $^  $  -Wl,--start-group $(ARCHIVE_LIBS) --end-group  -o $(TARGET)
        cp -f $(TARGET) ../../../bin/


Can some please throw some light on this? I had googled but I did not get any clue?

Thanks and Regards,
Souvik

---

