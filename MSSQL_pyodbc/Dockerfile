FROM ubuntu

RUN apt-get update 
RUN apt-get install python python-pip gcc g++ build-essential unixodbc-dev unixodbc-bin -y
RUN pip install pyodbc
RUN apt-get install curl -y
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

RUN apt-get update
RUN ACCEPT_EULA=Y apt-get install msodbcsql17 mssql-tools -y
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc


WORKDIR /usr/src/app
COPY . .

RUN python test_connect.py
