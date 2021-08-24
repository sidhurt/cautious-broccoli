# cautious-broccoli
Cricket control board would like to generate the list of all-rounder players for the selection in the cricket team based on following conditions.
#include<iostream> 
using namespace std; 
class Players 
{ 
    char name[40], region[20]; 
    float batavg, bowlavg; 
public: 
    void readData() 
    { 
        cout<<"Player Name:"<<endl; 
        cin>>name; 
        cout<<"Region:"<<endl; 
        cin>>region; 
        cout<<"Batting Average:"<<endl; 
        cin>>batavg; 
        cout<<"Bowling Average:"<<endl; 
        cin>>bowlavg; 
    }
    void sortList(Players players[]) 
    { 
        Players temp; 
        for (int i=0;i<5;i++) 
        { 
            for (int j=0;j<4;j++) { 
                if (players[j].batavg<players[j+1].batavg) 
                { 
                    temp=players[j]; 
                    players[j]=players[j+1]; 
                    players[j+1]=temp; 
                } 
            } 
        } 
        players[0].displayList(players); 
        for (int i=0;i<5;i++) 
        { 
            for (int j=0;j<4;j++) { 
                if (players[j].bowlavg>players[j+1].bowlavg) 
                { 
                    temp=players[j]; 
                    players[j]=players[j+1]; 
                    players[j+1]=temp; 
                }
            } 
        } 
        players[0].displayList(players); 
    } 
    void displayList(Players players[]) 
    { 
        for (int i=0;i<5;i++) 
        { 
            cout<<"Name:"<<players[i].name<<endl; 
            cout<<"Region:"<<players[i].region<<endl; 
            cout<<"Batting Average:"<<players[i].batavg<<endl; 
            cout<<"Bowling Average:"<<players[i].bowlavg<<endl; 
        } 
    }
void generateList(Players players[]) 
    { 
        int x=0; 
        for (int i=0;i<5;i++) 
        { 
            if (players[i].batavg>30 && players[i].bowlavg<25) 
            { 
                cout<<players[i].name<<endl; 
                x=1; 
            } 
        } 
        if (x==0) 
            cout<<"None"<<endl; 
    } 
}; 
int main() 
{ 
    Players 
    players[5]; 
    for (int i=0;i<3;i++) 
    { 
        players[i].readData(); 
    } 
    players[0].sortList(players); 
    players[0].generateList(players); 
    return 0; 
}
