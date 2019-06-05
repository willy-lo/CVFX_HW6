# CVFX_HW6
1.5% (Take videos by yourselves)

以下是我們拍的第一個影片，是投籃沒投進的影片，之後會用威力導演想辦法把球弄進，並把人的周圍加一些東西或記分板等等的效果。

https://www.youtube.com/watch?v=Qb7jmrn1PWs&feature=youtu.be

以下是我們拍的第二個影片，因為第一個影片動得比較快，導致她籃球或人的feature沒有辦法抓那麼好，所以我們拍了一個更慢的影片。

https://www.youtube.com/watch?v=H7q0gpGOy38&feature=youtu.be

2.10% (Make these visual effects with ORB-SLAM2)

3.10% (Make these visual effects with any post-production software)

第一個影片加得特效

https://www.youtube.com/watch?v=yJteCd0uQq0&fbclid=IwAR2AJnZnuRV0t_q0uMo0PcceG725PV-jgPcjphxorijma_tRjNQeZgVPD5g

4.10% (Compare above methods)

5.10% (Make some special effects based on the pose information, such as rotating, zooming in or out)

6.5% (Insert a 3D model to your video

7.10% (Bonus- Make visual effects with other SLAM methods.)

8.這次我們在環境上出了很多問題，所以將cmake的內容放上來讓大家參考，或許對解決環境的問題有更深入的了解

一、介紹

       “CMake”是“cross platform make”的縮寫，是一個跨平台的安裝（編譯）工具，可以用簡單的語句來描述所有平台的安裝或編譯過程。Cmake 並不直接建構出最終的軟體，而是產生標準的建構檔，如Unix 的makefile 或Windows的projects/workspaces，然後再依一般的建構方式使用。在輸出makefile或者project文件的同時，能測試編譯器所支持的C++特性。CMake 的組態檔取名為CmakeLists.txt，每個目錄一個。

       cmake 的特點主要有：

1 、開放源代碼，使用類BSD許可發布。http://cmake.org/HTML/Copyright.html

2 、跨平台，並可生成native編譯配置文件，在Linux/Unix平台，生成makefile，在蘋果平台，可以生成xcode，在Windows平台，可以生成MSVC的工程文件。

3 、能夠管理大型項目，KDE4就是最好的證明。

4 、簡化編譯構建過程和編譯過程。Cmake的工具鏈非常簡單：cmake+make。

5 、高效慮，按照KDE官方說法，CMake構建KDE4的kdelibs要比使用autotools來構建KDE3.5.6的kdelibs快40%，主要是因為Cmake在工具鏈中沒有libtool。

6 、可擴展，可以為cmake編寫特定功能的模塊，擴充cmake功能。

 

二、安裝

1 、安裝包安裝

       官網下載地址：http://wwwNaNake.org/HTML/Download.html

（1）下載CMake的安裝包，如cmake-3.4.3 tar.gz。

（2） 解壓縮：tar xvf cmake-3.4.3 tar.gz

（3） 進入解壓目錄：cd cmake-3.4.3

（4） 如果未安裝過CMake，則執行如下操作：

./bootstrap

         make

         make install

         如果安裝過CMake，並進行新版本的安裝，則執行如下操作：

cmake

         make

         make install

 

2 、在線安裝

       sudo apt-get install cmake

 

三、使用

CMake 的所有的語句都寫在CMakeLists.txt的文件中。當CMakeLists.txt文件確定後,可以用ccmake命令對相關的變量值進行配置。這個命令必須指向CMakeLists.txt所在的目錄。配置完成之後,應用cmake命令生成相應的makefile（在Unix like系統下）或者project文件（指定用window下的相應編程工具編譯時）。

其基本操作流程為：

$> ccmake directory

$> cmake directory

$> make

其中directory為CMakeLists.txt所在目錄；

第一條語句用於配置編譯選項，如VTK_DIR目錄，一般這一步不需要配置，直接執行第二條語句即可，但當出現錯誤時，這裡就需要認為配置了，這一步??才真正派上用場；

第二條命令用於根據CMakeLists.txt生成Makefile文件；

第三條命令用於執行Makefile文件，編譯程序，生成可執行文件。

 

四、常用指令

1 、PROJECT(工程名[CXX] [C] [Java])

    用於定義工程名字，並可以指定工程支持的語言，支持的語言列表可以忽略，默認支持所有語言。這條指令隱式定義了兩個cmake變量：

<projectname>_BINARY_DIR （二進製文件保存路徑）

<projectname>_SOURCE_DIR （源代碼路徑）

cmake 系統預定義了PROJECT_BINARY_DIR和PROJECT_SOURCE_DIR，其值與上述兩個變量對應。

 

2 、SET(變量名變量值)

SET(VAR [VALUE] [CACHE TYPEDOCSTRING [FORCE]])

       用來顯示的定義變量，如SET(SRC_LIST main.cpp a.cpp b.cpp)。在引用變量時使用${}，如${SRC_LIST}，但在IF控制語句中引用變量是直接使用變量名。

 

3 、MESSAGE(消息類型消息內容)

MESSAGE([SEND_ERROR | STATUS | FATAL_ERROR] "message to display")

       用於向終端輸出用戶定義的信息，包含了三種類型:

SEND_ERROR ，產生錯誤，生成過程被跳過；

SATUS ，輸出前綴為—的信息；

FATAL_ERROR ，立即終止所有cmake過程。

 

4 、ADD_EXECUTABLE(可執行文件名生成該可執行文件的源文件)

ADD_EXECUTABLE(main ${SRC_LIST})

用於生成一個文件名為main的可執行文件，相關的源文件是SRC_LIST中定義的源文件列表。

 

5 、ADD_LIBRARY(動態/靜態鏈接庫名生成動態/靜態鏈接庫的源文件)

ADD_LIBRARY(core SHARED ${ SRC_LIST })

ADD_LIBRARY(core STATIC ${ SRC_LIST })

用於生成一個文件名為core的動態/靜態鏈接庫，相關的源文件是SRC_LIST中定義的源文件列表。

 

6 、SET_TARGET_PROPERTIES(目標PROPERTIES選項動態/靜態鏈接庫名)

       SET_TARGET_PROPERTIES(core PROPERTIES OUTPUT_NAME "core_1")

       用於生成core_1動態/靜態鏈接庫。

SET_TARGET_PROPERTIES(core PROPERTIESVERSION 1.2 SOVERSION 1)

       用於設置動態鏈接庫版本號，VERSION指代動態庫版本，SOVERSION指代API版本。

 

7 、ADD_SUBDIRECTORY（子目錄名字）

       ADD_SUBDIRECTORY(source_dir [binary_dir] [EXCLUDE_FROM_ALL])

       用於向當前工程添加存放源文件的子目錄，並可以指定中間二進制和目標二進制存放的位置。EXCLUDE_FROM_ALL參數的含義是將這個目錄從編譯過程中排除。

 

8 、SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR} /bin)

用於更改生成的可執行文件路徑。

 

9 、SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR} /lib)

用於更改生成的庫文件路徑。

 

10 、INCLUDE_DIRECTORIES（追加標誌頭文件路徑）

       INCLUDE_DIRECTORIES([AFTER|BEFORE] [SYSTEM]dir1 dir2 ...)

       用於引入頭文件搜索路徑，路徑之間用空格分隔，如果路徑中包含空格，則路徑使用雙引號。

       可以通過兩種方式來進行控制搜索路徑添加的方式：

（1）CMAKE_INCLUDE_DIRECTORIES_BEFORE，通過SET這個cmake變量為on，可以將添加的頭文件搜索路徑放在已有路徑的前面。

（2）通過AFTER或者BEFORE參數，也可以控制是追加還是置前。

 

11 、LINK_DIRECTORIES（庫文件路徑）

       LINK_DIRECTORIES(directory1 directory2 ...)

       用於添加非標準的共享庫搜索路徑。

 

12 、TARGET_LINK_LIBRARIES（需要連接的文件動態/靜態鏈接庫）

       TARGET_LINK_LIBRARIES(target library1 <debug | optimized> library2...)

設置要連接庫文件的名稱。
