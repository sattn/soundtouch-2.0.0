[SoundTouch](http://www.surina.net/soundtouch/sourcecode.html)をndk-buildできるように修正しました。

## 主な変更点
soundtouch-2.0.0/soundtouch/source/Android-lib/jni/Android.mk
を以下のように変更しました。
```
###LOCAL_SHARED_LIBRARIES += -lgcc 
LOCAL_LDLIBS    += -lgcc 

###LOCAL_CFLAGS += -fvisibility=hidden -I ../../../include -fdata-sections -ffunction-sections
LOCAL_CFLAGS += -Wall -fvisibility=hidden -I ../../../include -D ST_NO_EXCEPTION_HANDLING -fdata-sections -ffunction-sections -marm
```

.hファイルについてもパスが正しくなるように修正しました。

> soundtouch-2.0.0/soundtouch/source/Android-lib/jni/soundtouch-jni.cpp.org

これは元ファイルですが、processFileでコンパイルエラーとなります。（戻り値の型誤り）

> soundtouch-2.0.0/soundtouch/source/Android-lib/jni/soundtouch-jni.cpp.org.edit

こちらが修正ソースです。

> soundtouch-2.0.0/soundtouch/source/Android-lib/jni/soundtouch-jni.cpp

これは、[VladimirKulyk](https://github.com/VladimirKulyk/SoundTouch-Android)さんのソースを拝借したものです。
バイトデータを処理する場合は、こちらのインタフェースが便利です。
