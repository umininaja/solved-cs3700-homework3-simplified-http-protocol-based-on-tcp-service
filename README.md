Download Link: https://assignmentchef.com/product/solved-cs3700-homework3-simplified-http-protocol-based-on-tcp-service
<br>
<strong>Part I: </strong>Write a <strong><em>client</em></strong> program and a <strong><em>server</em></strong> program to implement the following simplified HTTP protocol based on TCP service. Please make sure your program supports multiple clients. The webpage file CS3700.htm is provided. You may choose a port like 5678 and hard code it in both client and server programs. (Hints: for testing both programs on the same computer, you may want to put client program and server program at two different directories. Do NOT hard code the file name “CS3700.htm”!) • The <strong><em>ending signature</em></strong> of the <strong><em>entity body</em></strong> in the <strong><em>HTTP response message</em></strong> for the case “200 OK”:

<ul>

 <li>When the HTTP Server program sends a HTTP response message out, it pads four continuous blank lines, i.e., “r
r
r
r
”, to the end of the .htm file as the ending signature of the entity body.</li>

 <li>When the HTTP Client program read the HTTP response message line by line, it counts the number of <strong>continuous</strong> lines that are empty strings “” (NOT a null string). Once such number reaches 4, the entity body has been fully received.</li>

 <li>It is assumed that the .htm file does not include such ending signature (in the real practice, length of the entity body may be included in the head line and used to determine the end of an entity body).</li>

 <li><strong>HTTP Client Program: </strong>

  <ol>

   <li>Display messages on the standard output to ask the user to input the DNS name/ip of your HTTP server.</li>

   <li>Buildup the TCP connection to your HTTP server with the Host Name input by User at the given port, and display the <strong>RTT</strong> <strong>of establishing this TCP connection</strong> in millisecond (the difference between the moments right before and after creating the socket object). Catch the exception, terminate the program, and display error messages on the standard output if any.</li>

   <li>Display message<strong>s</strong> on the standard output to ask the user to input the HTTP method type, name of the htm file requested, HTTP Version, and User-Agent, <strong>respectively (separately please!)</strong>. (hint: all inputs can be strings.)</li>

   <li>Use the above inputs from user to construct ONE HTTP request message and send it to the HTTP server program over the TCP connection. Your HTTP request message only needs to include the following lines. (Hint: At the <strong>end of each line</strong> <strong>including the last empty line</strong>, a <strong>“r
”</strong> is needed. The correctness of the format will be checked by the instructor.):</li>

  </ol></li>

</ul>

The request line (hint: the URL should include a ‘/’ in front of the htm file name)

The header line for the field “Host:”

The header line for the field “User-Agent:”

&lt;empty line&gt;

<ol start="5">

 <li>Receive and interpret the HTTP response message from the HTTP Server program <strong>line by line</strong>, display the <strong>RTT </strong>(File Transmission Time may be included)<strong> of HTTP query</strong> in millisecond (the difference between the moment right before HTTP request is sent and the moment right after HTTP response is received) as a single line (e.g., RTT = 1.089 ms), display the <strong>status line</strong> and <strong>header lines</strong> of the HTTP response message on the standard output, and save the data in the <strong>entity body</strong> to a .htm file to local directory if there is any. (Hint: (a) When one empty string “” (NOT a null string!) is read the FIRST TIME, it indicates the header lines are over and the entity body is going to start next line if the case is “200 OK”.)</li>

 <li>Display a message on the standard output to ask the User whether to continue. If yes, repeat steps 3 through 6. Otherwise, close all i/o streams, TCP connection, and terminate the Client program.</li>

</ol>

<ul>

 <li><strong>HTTP Server Program</strong>:

  <ol>

   <li>Listen to the given port and wait for a connection request from a HTTP Client.</li>

   <li>Create a new thread for every incoming TCP connection request from a HTTP client.</li>

   <li>Read, display to the standard output, and interpret incoming HTTP request message line by line</li>

  </ol></li>

</ul>

o          If the method given in the request line is NOT “GET”, it is a “400 Bad Request” case o   If the file specified in the URL does not exit/cannot be open, it is a “404 Not Found” case o     Otherwise, it is a “200 OK” case

<ol start="4">

 <li>According to the case discovered above, construct ONE HTTP response message and send it to the HTTP client program over the TCP connection. Your HTTP response message needs include the following lines using the HTTP message format. (Hint: At the <strong>end of each line</strong> <strong>including those empty lines</strong>, a <strong>“r
”</strong> is needed.)</li>

</ol>

The status line

The header line for the field “Date:”

The header line for the field “Server: ”, you may use any value of your choice &lt;empty line&gt;

Data read from the requested HTML file line by line … (hint: for the 200 OK case only)

&lt;empty line&gt;

&lt;empty line&gt;

&lt;empty line&gt;

&lt;empty line&gt;

<ol start="5">

 <li>Repeat Step 3 through 4 until a null is read. (Hint: this happens when THIS client closes the TCP connection.)</li>

 <li>Close all i/o streams and the TCP socket for THIS Client, and terminate the thread for THIS client. (Hint: when this happens, the parent thread is still alive doing Steps 1 and 2 forever, unless the Server process is killed/terminated.)</li>

</ol>




<strong>Part II : Test your programs on the Virtual Servers in the cloud and your laptop/home computer. </strong>

<strong>Warning</strong>: to complete this part, especially when you work at home, you must first (1) <strong>connect to GlobalProtect </strong>using your NetID account (please read “<strong>how to connect to GlobalProtect …</strong>” at <u>https://msudenver.edu/vpn/</u>); then (2) <strong>connect to the virtual servers cs3700a and cs3700b</strong> using <strong><em>sftp</em></strong> and <strong><em>ssh</em></strong> command on MAC/Linux or <strong><em>PUTTY</em></strong> and <strong><em>PSFTP</em></strong> on Windows.




<table width="720">

 <tbody>

  <tr>

   <td colspan="2" width="720">ITS only supports GlobalProtect on MAC and Windows machines.  If your home computer has a different OS, it is your responsibility to figure out how to connect to cs3700a and cs3700b for programming assignments and submit your work by the cutoff deadline.  Such</td>

  </tr>

  <tr>

   <td width="320">issues cannot be used as an excuse to request any extension.</td>

   <td width="400"><strong> </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<ol>

 <li>MAKE a directory “<strong>HW3</strong>” under your home directory on <strong>cs3700a</strong>.msdenver.edu and <strong>cs3700b</strong>.msudenver.edu, a subdirectory “<strong>server</strong>” under “<strong>HW3</strong>” on <strong>msudenver.edu</strong>, and a subdirectory “<strong>client</strong>” under “<strong>HW3</strong>” on <strong>cs3700b.msudenver.edu</strong>.</li>

 <li>UPLOAD and COMPILE the <strong><em>server</em></strong> program under “<strong>HW3/server</strong>” and the <strong><em>client</em></strong> program under “<strong>HW3/client</strong>” on the VMs.</li>

 <li>TEST <strong><em>the</em></strong> <strong><em>server program</em></strong> running on <strong>cs3700a</strong>.msudenver.edu together with <strong><em>a client program</em></strong> running on your laptop or lab computer and <strong><em>another client program</em></strong>, simultaneously, running on <strong>cs3700b</strong>.msudenver.edu to test all the possible cases.</li>

 <li>SAVE a file named <strong><em>txt</em></strong> under “<strong>HW3/client</strong>” on <strong>cs3700b</strong>.msudenver.edu, which captures the outputs of your <strong><em>client</em></strong> program when you test it. You can use the following command to redirect the standard output (stdout) and the standard error (stderr) to a <strong>file</strong> on UNIX, Linux, or Mac, and view the contents of the file</li>

</ol>

<strong>java prog_name_args | tee testResultsClient.txt //copy stdout to the .txt file  //if you want, you may also use “script” command instead of the “tee” command </strong>

<strong>     //to write both stdin and stdout into testResultsClient.txt while testing your </strong>

<strong>      //client program on cs3700a.  For how to use “script”, see  </strong>

<strong> //</strong> <strong><u>https://www.geeksforgeeks.org/script-command-in-linux-with-examples/</u></strong><strong>  //or Google “script command in Linux” if the above link is broken. cat file-name //display the file’s contents.  </strong>